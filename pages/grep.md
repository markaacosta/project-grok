# grep

As essential as [find](find.md) is for *finding* things, this is how essential `grep` is for *filtering* lines of text produced by `stdout`.

## Basic usage

> this page assumes you already know at least the basics of [regex](regex.md)

A common pattern is: text has been produced on `stdout`, and we then wish to filter that output down and only show lines that *match some (regex) pattern*:

`cat file.txt | grep "est"`

> there are 50 lines in this file; only show lines that have the string `est` in them somewhere
>
> output is often <span style="color: red">colorized</span> to more easily emphasize result patterns:

![grep-basics](../assets/grep-basics.gif)

## grep - leading pattern

In the prior basic example, grep *trailed* the `cat` command; however, `grep`, like most any command, can also *lead*, and the filename could come after, with no `cat` command needed. What you use depends on the situation / convenience, and possibly personal preference.

`grep "est" file.txt`

![grep-basics-leading-version](../assets/grep-basics-leading-version.gif)

## recursive `grep`

Just as `find` can (recursively) find files and directories across the vast scope of a machine, `grep` too can recursively identify the *contents* of files, showing exactly which files contain a given pattern. This powerful feature allows for very quick and thorough searching:

![grep-recursive](../assets/grep-recursive.gif)

## `rg`

Learn `grep`; it is on nearly every Unix operating system. Once you are comfortable with it, consider [rg](ripgrep.md) (i.e. "ripgrep") instead for your personal machine. `rg` is like `grep`, but faster, more modern, and written with an (arguably) simpler and more usable syntax.