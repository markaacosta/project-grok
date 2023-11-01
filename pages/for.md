# Bash `for` loop

Like most programming / scripting languages, bash has a `for` looping construct; check the bash manual for full details [^1]

[^1]: https://www.gnu.org/software/bash/manual/bash.html#index-for

## `for` loop examples

examples of common ways a `for` loop might be used in practice:

### for *files in directory*

> this pattern uses *globbing* to select only files

`for file in *.*; do echo $file; done`

![for-files](../assets/for-files.gif)

### for *(sub)directories in directory*

> this pattern uses *globbing* to select only folders

`for dir in *.*; do echo $dir; done`

![for-dirs](../assets/for-dirs.gif)

### for *elements in bash array*

Yes, bash has an [array](bash-data-structures.md#bash-arrays). We can create and loop the array.

see [example](bash-data-structures.md#loop--iterate-an-array)

### for *elements in associative bash array*

TODO

### for *i in range*

> Python-style for loops, for simple 'loop N times', with or without the use of said N
>
> in this example, `$(seq 1 10)` is an expansion type called [command substitution](expansions.md#command-substitution), that first generates the numbers 1-10, *then* allows us to loop across them (in this case, we merely print the numbers as we loop them)

![for-i-in-range](../assets/for-i-in-range.gif)