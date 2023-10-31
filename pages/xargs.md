# Xargs

`xargs` is found on most Unix-like operating systems, and is one of the most powerful command-line tools. If you have multiple *things*, and you want to *do something* to *each* of those things, you can do so with `xargs`

# The xargs pattern:

> often, it's conventional to `find` items to process before using xargs to process them. Read about `find` first [here](find.md) if you haven't already

> `xargs` also makes heavy use of pipes; read about [them](pipes.md) first too if you haven't, then return here

The *find-xargs* pattern is very common, and very useful. We `find` some files and / or directories, then we can *do* something to them with `xargs`. The core syntax approach is:

`find /some/location [options] | xargs {cmd} [options]`

this is, "look [in] *some location* for *files and / or folders*; then, and *do something to them* using some *command* {cmd}"

# Examples

## pairing `xargs` with `find`

### get full paths for all text files in current directnory

`find * -type f -iname "*.txt" | xargs readlink -f`

![xargs-basic](../assets/xargs-basic.gif)

### "." vs "*" vs "/" in a `find` construct

see the [find subsection](find.md#location--vs--vs--in-a-find-construct) explaining this

## grokking other `xargs` concepts

### "all as arguments" vs "each as single argument" 

consider the `readlink` command in three contexts:

`readlink -f file1.txt`

![readlink-](../assets/readlink-single.gif)

`readlink -f file1.txt file2.txt file3.txt`

![readlink-](../assets/readlink-multi.gif)

`files=(file1.txt file2.txt file3.txt); for file in ${files[@]}; do readlink -f \"${file}\"; done`

![readlink-](../assets/readlink-multi.gif)

- the command works with one argument
- the command works just as well with multiple arguments 
- the command also works within a looping construct; the output is identical to the output of the second approach

The third approach (looping constructs) *always* works with this type of pattern; it's entirely generic. The first approach always works - any command that accepts a file as an argument is going to work if you only pass one file as an argument!

The second approach is trickier; some commands support multiple / indefinite arguments at the end, some do not.

How does this relate to `xargs`? You write xargs constructs differently depending on whether a command supports multiple trailing arguments like this or not. Let's see a failing case:

`find * -maxdepth 1 -type f -iname "*.txt" | xargs cp ./new_dir/`

`find` gets all text files in the current directory and passes them to `xargs`, which tries to copy them all to the `new_dir` directory.

![xargs-multi-fail](../assets/xargs-multi-fail.gif)

Why specifically does this fail? When these values get passed to `xargs`, it expands everything like this before running the actual `cp` command:

`cp ./new_dir file1.txt file2.txt file3.txt file4.txt file5.txt`

This is not what we intended; the *last* argument of copy is the destination, but our destination is not understood to be the final argument. `cp` has a solution for this - *explicitly* marking the `new_dir` directory as the *target* by using the `-t` flag before it. Doing this helps `xargs` understand that all the files we pipe in are *things to copy*, and `new_dir` is the *target* to copy them *to*. The command works now:

![xargs-cp-multi-with-t-flag](../assets/xargs-cp-multi-with-t-flag.gif)

This pattern of including the `-t` flag works for `cp`, but there are some commands that *only work* when a single argument is passed. Can we still get multiple items with `find` and use them all with `xargs` in this case? Yes we can; there is a general pattern that makes `xargs` compatible with these types of commands:

`find * -maxdepth 1 -type f -iname "*.txt" | xargs -I {} cp "{}" -t ./new_dir/`

![xargs-cp-multi-with-argument-substitution](../assets/xargs-cp-multi-with-argument-substitution.gif)

This more general approach will work in more cases; observe that we passed an `-I` flag with the argument `{}`; this flag (and argument) allow us to *substitute in* a value in our command that is located right where the actual file argument would be. Now `xargs` is told exactly where to put each argument, puts each argument there, and runs the command for every single argument. Everything works. Hopefully this has helped you understand how to get `xargs` to play nicely with different kinds of commands. In short:

> for commands that can only handle single arguments, use the `-I` flag and a substitute value like `{}`

> for commands that handle multiple arguments well, piping to `xargs` can be done without this flag.

### handling problematic characters / spaces / etc.

> this is part of a much larger set of problems you need to solve when working on the command line - for full details, see the page on [handling shell expansion(s)](anatomy-of-problematic-shell-expanions-and-how-to-deal-with-them.md).

#### Strategy 1 - Double-quote for proper expansions

A common cause for xargs failures (and shell failures in general) is the improper handling of spaces. The short version: spaces can be part of directory names or file names, but are *also* the primary way shells separate [words](words.md).

`find *-maxdepth 1 -type f -iname "*.txt" | xargs readlink -f`

![xargs-issue-spaces-in-filename](../assets/xargs-issue-spaces-in-filename.gif)

In the interactive example above, observe how `file_one.txt` and `file_three.txt` are interpreted properly, but the file with a space in its name (`file two.txt`) is not; when we run the command, the shell thinks it's two different files, one named `file`, and one named `two.txt` - because shells use spaces to figure out where one token ends and another begins.

> /home/marka/Desktop/temp/Public/deeper/file_one.txt
> /home/marka/Desktop/temp/Public/deeper/file_three.txt
> /home/marka/Desktop/temp/Public/deeper/<span style="color: red">file //problem!</span>
> /home/marka/Desktop/temp/Public/deeper/<span style="color: red">two.txt //problem!</span>

How do we get around this common issue? If you're writing a piece out literally, simply wrap the offending piece in *double-quotes*. For example:

~~readlink -f file two.txt~~

**readlink -f "file two.txt"**

If you're using `xargs`, use a substitute value and wrap *that* in double-quotes.

`find *-maxdepth 1 -type f -iname "*.txt" | xargs -I {} readlink -f "{}"`

![xargs-handle-issue-spaces-in-filename](../assets/xargs-handle-issue-spaces-in-filename.gif)

#### Strategy 2 - Nul-terminated sequences

Sometimes even with double-quotes for handling space characters, there are still other non-alphabetic characters that can cause issues with how the shell interprets words / tokens. A more robust way to handle complex cases like this is to use <mark>nul-terminated sequences</mark> instead. A nul-terminated sequence replaces all (non-visible) *newline characters* (`\n`) with the nul character (also non-visible, represented as `\0`).

While it's more to type, this pattern generally 'just works' for usual tedious shell expansion cases - it is supported by most tools where you imagine it would be useful (e.g. `find`, `ls`, `xargs`, `grep`, etc.)

Using our current example, here's how we would write it out. Notice that we enable the nul behavior both for the preceeding `find` command (with `-print0`), and for the receiving `xargs` command as well (with `-0`).

`find * -maxdepth 1 -type f -iname "*.txt" -print0 | xargs -0 -I {} readlink -f "{}"`

![xargs-nul-terminated-sequence-example](../assets/xargs-nul-terminated-sequence-example.gif)

### Simpler Syntax for Common Tasks

Suppose you have a text file named `websites.txt` with a URI on each line. You can perform a `ping` test on every site like so:

`cat websites.txt | xargs -I {} ping -c 1 "{}"`

Often this pattern of xargs on the right side of a pipe occurs; however, in many cases, we can also simplify the syntax and lead with `xargs`:

`xargs -I{} ping -c 1 "{}" < websites.txt`

![xargs-as-syntax-leader](../assets/xargs-as-syntax-leader.gif)

This is slightly more correct; rather than printing the text file to `stdout` on the terminal and then reading form a pipe, we lead with `xargs`, and pass the text file directly as an input from `stdin` (via the `<` operator).

### Simpler Syntax for Restricting to N Args Per Xargs Call

We learned about using a *substitution value* with xargs (often, by convention, `{}`). This is critical for writing expressions where the location of the substitution matters and may not be clear to xargs. When we merely wish to restrict the amount of arguments xargs can take per invocation (for instance, to '1'), we can simply use the `-n` flag:

instead of:

`xargs -I{} ping -c 1 "{}" < websites.txt`

we can write:

`xargs -n 1 ping -c 1 < websites.txt`

### Creative Xargs Case: Restrict Output Groups

TODO

## Miscellaneous `xargs` concepts / tips:

### Ensure alias expansion for tokens succeeding the `xargs` keyword

By default, as a consequence of how `aliases` work, words written after the `xargs` keyword do not get expanded; so, if you use aliases for any common commands, they will not work with xargs as you expect them to. This can be avoided by creating an alias for `xargs` itself (and perhaps placing this alias in the `~/.bashrc` file):

`alias xargs='xargs '`

Aliases will now work as you expect.