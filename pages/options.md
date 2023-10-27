# Options

There are different types of shell options:

## `set` options

`set` enables (or disables) options from `sh`, `bash`'s predecessor

### list `set` options

`set -o`

### enable a `set` option

`set -o {option}`

### disable a `set` option

`set +o {option}`

### some useful `set` options

#### noclobber

`noclobber` allows that TODO

## `shopt` options

`shopt` enables (or disables) options new to `bash`, i.e. options that are not in the `sh` shell

### list `shopt` options

`shopt`

### enable a `shopt` option

`shopt -s {option}`

### disable a `shopt` option

`shopt -u {option}`

### some useful `set` options

TODO

### Option Persistence

These options are enabled in a shell but cease to be applied when that shell is closed. To persist these values and have them in all shells that you open, write the various 'enable' commands to your [.bashrc](../pages/bashrc.md) file.