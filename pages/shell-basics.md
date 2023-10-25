# Shell Basics

## Some terminology

We've so far used the terms *shell*, *command-line*, and *terminal* to talk about issuing commands to a machine. These terms are sometimes used interchangeably. In general (and throughout this work), they are differentiated and defined and follows:

- shell - the actual tool used to issue commands to a machine
- terminal - an *emulator* a shell runs in. On modern computers, to use a shell, in almost all cases a terminal will be opened
- command line - a more generic term for doing things in a terminal-like environment, i.e. without a GUI and mouse

## Absolute basics / first steps

A natural starting point for using a shell is *file operations* - creating, copying, moving, deleting, or otherwise manipulating files and directories on a system; all computer users have performed these operations. We'll see how they're done on the shell.

### Viewing

```bash
ls
```

list the contents of the current directory

![ls](../assets/ls.png)

```bash
ls -l
```

Longer variation on the previous command; this one uses a [flag](nolink) (the "-l" flag) to list a `l`onger version of the same contents, with more details:

![ls-l](../assets/ls-l.png)

```bash
ls Apps
```

Provide `ls` a path and it will show the contents of *that* path rather than the current path / directory.

![lsdir](../assets/ls-dir.png)

### Changing directories

```bash
cd {some_directory}
```

After changing the directory, we see that the contents reflect that change.

![cd](../assets/cd.png)
### Creating / Copying

```bash
touch {somefile}
```

Create a file named `{somefile}`
![touch](../assets/touch.png)

```bash
cp example.txt Apps
```

Copy the file to another directory (`Apps`)

![cp-1](../assets/cp-1.png)

## Shortcuts for directory names, etc.

There are many convenient shortcuts for common directory patterns. See [directory expansions](expansions.md#directory-expansions).