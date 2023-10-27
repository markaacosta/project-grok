# Anatomy of A Command

Typing out and running commands is an essential aspect of command-line usage. All commands follow a similar, almost universal pattern:

**{CMD}** <span style="color: orange;">-{short_option(s)}</span > <span style="color: magenta;">--{long_option(s)}</span> <span style="color: cyan;">[argument(s)]</span>

What this means is, a `CMD` always starts with the name of the command itself, followed by some number of short and / or long options, followed by some number of arguments. 'Some number' of options or arguments could be zero, in either case! These are examples of what each would look like in practice:

- command: `ls`
- short option: `-e`
- long option: `--example`
- short key=value option: could be any of the following
  - `-r W`
  - `-r West`
  - `-rW`
- long key=value option: `--region West`
- argument: could be any of the following:
  - `- {file_name} (one or more)`
  - `- {directory_name} (one or more)`

As always, concrete examples are helpful:

`ls -a`: short option

> option to show ALL (a) with ls, rather than not showing hidden files / directories, the default behavior

`ls --all`: long option

> identical to above, but with long option version instead of short option. Long options are clearer, but less quick to type

`ls Apps`: (single) argument

> there are no *options* in this command, but there is an *argument*; instead of viewing the current directory (`ls`), we're telling `ls` to show us what's in the `Apps` folder instead.

`cp somefile.txt Apps`: (multiple arguments)

> here, we have *two* arguments; `somefile.txt`, and the `Apps` folder. Makes sense, since we're copying the file *into* the folder: `cp somefile.txt` would make not work, we need to copy the file to *some other location* for the command to work.

`rsync -avzn --stats --delete /some/place/dir1 /some/place/dir2`: multiple short and long options, multiple arguments

> a more complicated example: here, we are using short and long options with the `rsync` command, then provided two `folders` as arguments. This will sync make `dir` and exact copy of `dir2`, syncronizing their contents. The exact meaning of the flags is not relevant to the discussion scope.

## Summary

With these examples, the pattern should be clear; a command is always provided, then *flags* *may* <mark>alter</mark> that command's behavior; that's what flags do. Lastly, in many (not all) cases, we provide *arguments*; the items that the command will <mark>act on</mark>, or change in some way.