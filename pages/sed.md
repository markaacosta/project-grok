# `sed`: the <span style="color: purple">s</span>tream <span style="color: purple">ed</span>itor

As essential as [find](find.md) and [grep](grep.md) are for *finding* and *filtering* things to `stdout`, that's how essential `sed` is for taking `stdout` (or the contents of text files) and *changing* them; just like `grep` uses [regex](regex.md) to *filter* lines, `sed` uses perl substitution strings and regex patterns to *change* lines.

## Basic usage

Owing to its power and flexibility, `sed` has many different basic cases:

### deletions

> for some examples, we'll use [delta](delta.md) and [process substitution](process-substitution.md) to make it easier to view the differences between how a file looks before and after our changes with `sed`

`sed "2d" file.txt`

> delete 2nd line of `file.txt`

![sed-del-num](../assets/sed-del-num.gif)

`sed "1,3d" file.txt`

> delete lines 1 through 3 (inclusive) of `file.txt`

![sed-del-range](../assets/sed-del-range.gif)

`sed "/con/d" file.txt`

> delete lines containing "con" from file.txt

![sed-del-pattern](../assets/sed-del-pattern.gif)

### substitutions

Like some other Unix tools, `sed` uses *perl syntax* for its substitutions, which is like this:

`{op}/that/this/[g]`

in this syntax, `{op}`  is some *operation to perform*; since we want to *s*ubstitute, we would use `s` here. *That* is something we search for in the text, and *this* is the token with which we replace occurrences of *that*. The optional global `g` flag at the end means instead of replacing one occurrence per line, replace *all* occurrences per line, regardless of how many. An example:

`cat file1.txt | sed "s/replaceme/changed/g"`

> in file `file1.txt`, replace all occurrences of "replaceme" with "changed"
>
> we'll also pipe to `grep` just to filter output / show the changes more dramatically:

![sed-basic](../assets/sed-basic.gif)

## sed - leading pattern

In the prior basic example, sed *trailed* the `cat` command; however, `sed`, like most any command, can also *lead*, and the filename could come after, with no `cat` command needed. What you use depends on the situation / convenience, and possibly personal preference.

`sed "s/replaceme/changed/g" file1.txt`

![sed-basic-leading](../assets/sed-basic-leading.gif)

## Persistence

When we run `sed`, it doesn't change the original file, just what we see printed to `stdout`; once what we're seeing matches what we expect, and if we do what to change the actual file, we simple pass the `-i` flag:

`sed -i "s/replaceme/changed/g" file1.txt`

## substitution syntax - an alternate approach:

While using `/` as the perl substitution separator is conventional, it also means having to *escape* literal forward-slash matches without the substitution patterns themselves. Sed only requires a sepatator, the character can be arbitrary; consequently, using another character is recommended. One that is visually appealing and readable is the *pipe* (`|`):

`s|that|this|[g]`

## `sd`

Learn `sed`; it is on nearly every Unix operating system. Once you are comfortable with it, consider [sd](sd.md) instead for your personal machine. `sd` is like `sed`, but faster, more modern, and written with an (arguably) simpler and more usable syntax.