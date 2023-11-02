# find

Often, we want to do something to make files or directories; first we have to *find* them. For this reason, `find` is one of the tools used most often on Unix systems; it can be safely said that it's an indispensable tool: learning it well (at least the basics) is critical.

## the `find` pattern

The `find` pattern is relatively straightforward:

`find {some_location} [options] {thing(s) to find} [execution]`

This is to say, in most cases, we are *finding* some *things to find*, (in) a *location*, subject to some (optional) *options* flags; at that point, we may also *execute* some action on these items using `find` itself, or perhaps pass the results using a [pipe](pipes.md) along to some other command (often [xargs](xargs.md)).

For example, find all *directories* in (not below) the `$HOME` directory, and print out the full paths for each of them:

`find . -maxdepth 1 -type d -exec readlink -f {} \;`

let's decompose the command:

> - `find .` - find in the current directory
> - `-maxdepth 1` - prevent `find` from recursing, its [default behavior](find.md#find---recursive-by-default).
> - `-type d` - only find items that are of type *directory*
>   - you can find other types too; `f` for (regular) *file*, `l` for ([symbolic](links.md)) *link*, etc.
> - `-exec {some_cmd} {} \;` - run `{some_cmd}` once for each found item

## find - recursive by default

Unlike some tools (e.g. `cp`), `find` does not require a flag like `-r` in order to search recursively; in fact, `find` searches recursively by default, and only stays within the current folder if you tell it to using a *depth* flag, like so:

`find . -maxdepth 1 ...`

## find trailing constructs - `"\;"` vs `"\+"`

`find` commands that use `exec` always have `{some_command}`, and a <mark>trailing construct</mark>.

To illustrate differences, let's say `find` finds 10 files; each trailing construct will handle these 10 results differently:

`"\;"` - run {some_command} 10 times: one time per result

`"\+"` - run {some_command} one single time, with all 10 files as arguments

see the applicable [section](xargs.md#all-as-arguments-vs-each-as-single-argument) of the xargs page for a comparable binary (`xargs` too has the ability to handle all arguments at once, or each individually).

## location: `"."` vs `"*"` vs `"/"` in a `find` construct

You'll see find constructs start with `find .`, `find *`, or even `find /`; what is the difference?

- `find .` - find starting with the current directory itself, and include hidden files
- `find *` - find starting with *non-hidden* the *contents* of the current directory
- `find /` - find starting from the root of the filesystem. This is usually not what you want

## `fd`

Learn `find`; it is on nearly every Unix operating system. Once you are comfortable with it, consider [fd](fd.md) instead for your personal machine. `fd` is like `find`, but faster, more modern, and written with an (arguably) simpler and more usable syntax.