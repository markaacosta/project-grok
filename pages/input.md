# Input / Keybinds

Many unix programs use `readline` to control input / keybinds; this includes `bash` itself. For such programs, an `etc/inputrc` file can change system-wide key bindings, and for bindings specific to a user, `~/.inputrc` can be used.

## Bind syntax

### 'Keyname' Syntax

Keyname syntax can be written using *keyname* syntax, which is quite readable. Examples:

`Control-u: {cmd}`

> run {cmd} with `ctrl-u`

`Control-del: {othercmd}`

> run {othercmd} with `ctrl-del`

### 'Keyseq' Syntax

Keyseq syntax is less readable, but more flexibile, and is used in bash bindings. Examples:

`'"\C-a":"{cmd}"'`

> run {cmd} with `ctrl-a`

`'"\eb":"{othercmd}"'`

> run {othercmd} with `alt-b OR esc-b`

\* notice that "control" bindings have a trailing hyphen, and this is not the case in "meta / alt / escape" bindings \*

## Bash bindings

Bindings can also be made directly to `bash`, using the same syntax described above, but preceeded by a `bash -@` construct, where `@` is some letter option

### bash binding examples

`bind -r '\C-T'`

> remove action(s) bounded to `ctrl-t`

`bind -x '"\ef":"{cmd}"'`

> open {cmd} with `alt-f`, or `esc-f`

`bind -x '"\er":"$HOME/path/toscript/somescript.sh"'`

> run `{somescript.sh}` with `alt-r`, or `esc-r`

`bind -m vi-insert 'Control-l: clear-screen'`

> when in *mode* `{vi}`, use `ctrl-l` to clear the screen

## Persistence

to persist these settings so they are always present in new shells, write them to `~/.inputrc`, unless the bindings are for `bash` only; in that case, write them to `~/.bashrc`, or write them elsewhere and [source](../pages/sourcing.md) them in `~/.bashrc`.