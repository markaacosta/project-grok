# Pagers

## less

When the output of a command is too long to read, we can send it to a pager, allowing for reading the output with up and down arrows on the keyboard. `less` is a commonly-used pager you probably already have installed:

`lscpu | less`

![pager-less](../assets/pager-less.gif)

### less: basic usage

In less, move up and down with arrow keys, quit using [common quit patterns]

## bat

Among other things, `bat` is a modern pager written in Rust with more features, such as outlines, syntax highlighting, etc (see [modern-unix](modern-unix.md) for more information about `bat`). 

`lscpu | bat`

![pager-bat](../assets/pager-bat.gif)