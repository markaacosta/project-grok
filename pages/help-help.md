# "Help" Help

Learning the command line is a process; it's important to learn *how* to learn things with the manuals and tools provided in the shell itself. 

## `man` pages

For any given command `cmd`, you can get help with that command by opening the manual. This is done with `man {cmd}`:

`man ls`

![man-ls](../assets/man-ls.gif)

## `-h / --help` pages

Some commands don't have a `man` page; as an alternative (or supplement), you can use a `help` flag. This will take different forms depending on how a command was written, but usually it's either `{cmd} -h` or `{cmd} --help`:

`rg -h`

![rg-h](../assets/rg-h.gif)

Notice this prints the whole help page and takes us to the bottom; we must scroll up to the top to read from there. To make this easier, we'll open it in a pager like `less` instead, then move up and down with arrow keys:

`rg -h | less`

![rg-h-less](../assets/rg-h-less.gif)

## `apropos`

If it's unclear what tool could help solve a task, `man` pages have descriptions that can be searched with `apropos`:

`apropos video`

![apropos](../assets/apropos.gif)