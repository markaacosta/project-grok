# Exit Status / Codes

Bash scripts and functions can return <mark>exit status</mark>; exit status is a numeric value between 0 and 255. These values are used to indicate *what happened during the execution of said script or function.

By convention, returning with `0` indicates success, and all other values indicate some kind of failure; what kind of failure depends on the program (see the documentation for the applicable program).

## `exit` vs. `return` keyword

Both keywords pass execution back to the caller; however, `return` should be used when merely leaving a *function*, whereas `exit` is used for leaving a *script* entirely.