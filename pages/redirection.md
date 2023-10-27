# Redirection

[Streams](../pages/anatomy-of-input-output-and-other-streams.md) have default behaviors. `stdout` and `stderr` print to the screen. `stdin` passes input to a command. <mark>Redirection</mark> allows for additional and very useful behavior.

## write `stdout` to a file

Anything written to the screen with commands can be captured and saved in a text file. For this, all we need is the `>` operator. This operator is a shorthand that means "*take whatever is produced on the left and right it to the file on the right*".

> this file does NOT need to exist prior, if it doesn't exist, it will be created as a result of using `>` in this way

> `>` is actually a shorthand for `1>` (`1` means *standard output*) - if you type that instead, it will work the same way

For instance, write the names of all files in the current directory to a text file:

`find * -maxdepth 1 -type f > somefile.txt`

![stdout-to-file](../assets/stdout-to-file.gif)

## capture `stderr` in a file

Just like `1>` or `>` (shorthand) mean to redirect *standard output*, you can also redirect *standard error*; standard output is represented by a '1', standard error is represented by a '2':

![stderr-to-file](../assets/stderr-to-file.gif)

> this is a very useful pattern; we can run a very complex command, expected to produce a lot of output, and capture all the errors in a text file to look at later, separately from the non-error output that just prints to the screen.
>
> like with `stdout` redirection, this file does NOT need to exist prior, if it doesn't exist, it will be created as a result of using `>` in this way

## capture `stdout` AND `stderr`

Send everything to a file; you will see nothing on-screen, it will all be written to the file to which you are redirecting:

![stdout-and-stderr-to-file](../assets/stdout-and-stderr-to-file.gif)

## Append Operator `>>` and caution with `>` operator

Caution is advised when writing to file with `>`; if file doesn't exist, it will be created and written to. If file *does* exist, and contains text, that text will be overwritten in favor of new text; it is easy to permanently overwrite text you want to keep.

A way to prevent this (and useful technique in its own right) is to *append* to file rather than *write*. When we *append*, we add to the existing file content instead of overwriting it:

![append](../assets/append.gif)

> this behavior can be changed / avoided if the user enables the [`no-clobber`](../pages/options.md#noclobber)  `set` option.

