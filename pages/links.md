# Links

A core Unix filesystem concept is <mark>links</mark>. A *link* is a pointer to a file. Links can be *soft* or **hard**:

## Hard Links

A **hard link** is a reference to the actual *inode* of a file. A hard link is an actual file with file contents, just like the file it is created to reference. 

## Soft Links / Symlinks

A *soft link* (also called a '*symbolic link*', or '*symlink*' for short) is a pointer to a file, not an actual file itself; in this way, a *soft link* is like a *shortcut* on the Windows operating system, or an *alias* on MacOS.

### Creating links:

Creating a link is simple:

`ln /path/to/existing/file name_of_link`

This link will be a hard link; to make a soft link, simply employ the `-s` flag in a command that is otherwise the same:

`ln -s /path/to/existing/file name_of_link`