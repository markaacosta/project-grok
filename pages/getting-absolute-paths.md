# Getting Absolute Paths

In certain situations, it can be beneficial to get an absolute path to a file; however, many tools provide a relative path. Depending on the situation, we can still get a full path in various ways:

## absolute paths with `readlink`

`readlink -f {somefile.txt}`

> The `readlink` command allows us to get a file's full path:

![absolute-path-with-readlink](../assets/absolute-path-readlink.gif)

## absolute paths with `find`

`find "$(pwd)" -type f -iname "*.txt"`

> Sometimes we're writing a `find` construct; in these cases, we can still get the full path(s):

![absolute-path-with-find](../assets/absolute-path-find.gif)

## absolute paths with `fd`

`fd -a -t f "txt$"`

> With `fd`, it's also trivial to get the full path(s):

![absolute-path-with-fd](../assets/absolute-path-fd.gif)