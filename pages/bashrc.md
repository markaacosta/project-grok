# `.bashrc` file

When we make changes to our shell, we often want to keep them so they will always be applied every time we open a new shell; this can be done by writing those changes to our `.bashrc` file. This file is located in the `$HOME` directory, but is, due to the preceeding `.` character in the filename. With a `.bashrc` file, we the shell is customized, it retains those changes.

## re-sourcing

Whenever we make any changes to our `.bashrc` file (or to and file sourced *within* the `.bashrc` file), to see / make use of the changes, we must either open a new shell, or *re-[source](sourcing.md)* the `.bashrc` file in our current shell:

`source ~/.bashrc`

## running a non-customized shell

In certain situations it may be useful to run the shell without any of our `.bashrc` additions and changes; to run a shell without these:

`bash --norc`