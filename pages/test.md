# the `test` builtin

`test` allows for conditional expression evaluation outside a conventional `if / else` construct; use it to evaluate the boolean value of anything.

When `test` runs, it passes the boolean evaluation result to an [exit code](exit-status.md), with a value of `0` for TRUE and `1` for FALSE, as is common in other languages. We can echo the exit code directly after running the `test` command; an easier way is to simply append `&& echo yes` to the end of our command(s). If we see the 'yes' message, we know it's true, otherwise it's false.

`test 5 -gt 3 && echo yes`

> here we test that 5 is greater than 3, using bash comparison operators[^1]

![test-builtin](../assets/test-builtin.gif)

[^1]: https://www.gnu.org/software/bash/manual/bash.html#Bash-Conditional-Expressions