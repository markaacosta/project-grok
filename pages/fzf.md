# Fzf

## What Is `fzf` / why `fzf`?

[fzf](https://github.com/junegunn/fzf) is a widely-used, fast, and powerful interactive unix filter; like with an interactive filter, we insert fzf between [pipes](pipes.md) and [subshells](subshells.md) in order to make arbitrary selections before the rest of a command (or chain of commands) is interpreted.

There are other unix filters like [fzy](https://github.com/jhawthorn/fzy) and [pick](https://github.com/mptre/pick); why are we focusing on `fzf`? `fzf` is:

- ubiquitous
- portable
- highly configurable

As you might imagine, the principles we learn with `fzf` will apply to other filters / fuzzy finders; the generic nature of the underlying principles is what makes these filters / finders so powerful and useful.

We will best understand the basic concept (utility) with an example:

`fd -t f "txt$" | fzf | xargs readlink -f`

![fzf-first-example](../assets/fzf-first-example.gif)

The power of filters is that we can select the items *interactively* after we've already started running a command sequence. During this interactive selection phase, we can even search / filter down the results even further before making our selections with the \<tab\> key.

> this top-down, custom-size layout and the ability to make multiple selections with the \<tab\> key are not default behaviors; this is how they're achieved (perhaps add this as an alias for `fzf` in your `~/.bashrc` file?):
>
> `fzf -p 65%,75% -m --layout=reverse`

## More examples of how to use fuzzy pickers

### fzf in a [subshell](subshells.md)

```bash
for file in $(find * -maxdepth 0 -type f | fzf); do file "$file"; done
```

TODO - more examples
![fzf-in-subshell](../assets/fzf-in-subshell.gif)

## Standard caution for handling shell expansion(s)

As with all things on the command-line, fzf can be subject to issues with [shell expansion](anatomy-of-problematic-shell-expanions-and-how-to-deal-with-them.md#handling-problematic-shell-expansions). The preceding link will explain how to handle these things.

As you might imagine, for more complex handling, `fzf` includes a nul option that plays well with other commands; for instance:

fd -t f --max-results 10 | fzf <span style="color: purple; font-weight: bold">--print0</span> | xargs -0 -n 1 readlink -f

## Customizing the default options

In some apps, all customization is done manually with an [alias](aliases-and-shell-functions.md#aliases); in `fzf`, it's easier to customize default behavior on each run of the program:

> If the `FZF_DEFAULT_OPTS` variable is exported to the environment (from the `~/.bashrc` file, for instance), you can set default behavior(s). Here are some I've set up, which afford additional keybinds in the fuzzy picker, color in `bat` previews, etc.

```bash
export FZF_DEFAULT_OPTS="
-m --height 100%
--preview 'bat -n --color=always {}'
--preview-window hidden
--bind 'ctrl-y:execute-silent(printf {} | cut -f 2- | xclip -r -sel c)'
--bind 'ctrl-p:toggle-preview'
--bind 'alt-l:clear-query'
--bind 'alt-c:clear-selection'
--bind 'alt-a:toggle-all'
"
```

## the `fpp` case

In the particular case where you expect `stdout` to have *lots* of output, and *some* of that output to be file paths, we [fpp](fpp.md) is a fuzzy picker uniquely suited to the task of automatically finding what is `stdout` may be a file, letting us interactively select from these, then, if needed, so something to them.