# Aliases and Shell Functions

In any programming language, <mark>functions</mark> are a way to wrap functionality and increase the usability of said functionality; in bash, <mark>shell functions</mark> work the same way. <mark>Aliases</mark> perform a similar role, with greatly reduced functionality.

## Aliases

> an *alias* is just a shortcut for longer command text that expands on the shell when you type and execute it; that's it 

some examples of potentially useful aliases:

```bash
alias open='xdg-open'
alias off='shutdown -h now'
alias lock='xdg-screensaver lock'
alias toss='trash-put'
alias edit="$EDITOR"
```

## Shell Functions

Shell functions are just that: *functions*, with the same basic use pattern one would expect from other languages (functions can be *called*, arguments can be passed, etc.).

> it should be noted that bash functions *cannot* return values; like other things in Linux, everything is textual. Still, the last line of a function could echo a value, and this value could be capture in a variable in the calling scope; this will approximate conventional "return" behavior.
>
>In bash, the `return` keyword has another meaning: [exit status](../pages/exit-status.md)

an example of a function that performs a few routine `git` actions together, while allowing the user to enter a commit message when calling the function:

```bash
function gitroutine() {
  git add . && git commit -m '$1' && git push && git status
}
```

> notice that arguments are accessed in-function as `$n`, where `n` is a number starting at '1', and incrementing by one for each subsequent positional argument
>
> to call the above function in a script or interactive shell would look like:

```bash
gitroutine "and...here is the commit message"
```