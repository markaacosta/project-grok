- [ ] intro / forward (write at the end) - why you wrote this, how it's used, what it is and isn't, etc. make sure people know that it's *opinionated*, your view and good and useful tools and approaches in standard unices
- [x] meta of helping self on the cli - man, -h , manswitch, apropos, etc.
- [x] less pager and how to navigate (for man pages, etc.)
- [x] globbing / brace expansion
- [ ] why do things on the terminal?
- [x] modal editing
- [ ] vim / neovim
- [x] vim configs - "IDE" stuff
- [ ] scripting - how to write, test, debug scripts, etc.
- [ ] scripting - practical examples
- [ ] bootstrapping / getting up and running with the shell (e.g. unattended reinstallation, dnf install *, etc.)
- [ ] different distros - which, why, etc.
- [ ] `at` command
- [ ] `cron`
- [x] basic command-line patterns (cmdname -flags file|path ...)
- [x] redirection (to stdout, err, etcff.)
- [x] bind -X / inputrc / bind -P -p -S -s etc.
- [x] process substitution
- [x] absolute paths with find and fd
- [ ] different terminals by operating system (e.g. kitty for linux, wezterm for windows, etc.)
- [x] the $PATH - what, why, etc.
- [ ] bash - why bash (uniquitous)
- [x] wsl (praise be)
- [x] job control / process management (fg / bg / disown / etc.)
- [x] aliases
- [x] sudo / su
- [ ] bashc emacs / 'modifier' shortcuts to delete / move at word boundaries / etc.
- [ ] history - conventional, and interactive
- [ ] ch{mod,own}, permissions, etc.
- [x] pipes
- [ ] common tools and (OR?) core utils - will be HUGE (tac, uniq, ......)
- [ ] builtins
- [x] streams (out, in, and err)
- [ ] critical shell shortcuts (bring last arg, etc., comment line, etc.)
- [ ] shell interactive features (edit in $EDITOR before run, etc.)
- [ ] shell expansion and how to handle it (double quotes, escaped chars, etc)
- [ ] history expansion (last arg, etc.)
- [ ] (leveraging) completions
- [ ] dotfiles and how they work (bashrc, etc, your pattern for managing, etc.)
- [ ] chezmoi
- [x] sourcing / scope
- [ ] terminal flair (custom prompt, etc)
- [ ] modern *nix (fg, rg)
- [ ] quality-of-life - fzf, tldr, etc.
- [ ] tui apps - why, when / use cases, good tools
- [ ] fzf - the hidden / extra stream (technically a unix filter)
- [ ] gnome / dconf / etc.
- [ ] package managers / how they work in general
- [ ] comparison operators as short-circuits
- [ ] 'test' builtin
- [ ] subshells
- [ ] WORDS. how they work, how the shell attempts to understand them, etc.
- [ ] ssh - tunneling, X display forwarding, etc.
- [ ] replace from last command (^this^that)
- [ ] rsync
- [ ] globbing versus big-bro REGEX and why the latter is so important
- [ ] how regex works differently in different tools
- [ ] regex basics (this guide covers EVERYTHING i know / value with medium detail, it is expected that reader go elsewhere for more information on a given thing. and often, i'll link a good resource or two as section footnotes)
- [ ] xargs, xargs alias (see your aliases file) god of pipeline-building, and it's (limited) alternative, find / fd -exec
- [ ] null-terminated sequences, how they're useful in fzf for example, etc.
- [ ] null-terminated vs quoting things the shell could expand, etc.
- [ ] common cases for for loop (for FILES, for DIRS, etc.)
- [ ] common cases for while loop (reading LINES, etc.)
- [ ] return codes / checking success of command
- [ ] command chaining = semicolon versus hard AND
- [ ] the redirect errors pattern - useful for checking particular failures
- [ ] shopt / some of the more useful ones
- [ ] vim mode in shell!
- [ ] key (re)binding, both in bash, and, at a lower-level, inputrc
- [ ] the utility of full filepaths in find and fd
- [ ] resourcing, exec bash, etc.
- [ ] bash arrays and dicts
- [ ] elegant wants to move around (fuzzy dirs, fuzzy files, etc.)
- [ ] tui file managers - when ad-hoc is (temporarily better)
- [ ] loops
- [ ] conditionals
- [ ] comparison operators
- [ ] while (using it for reading lines, NOT for loops, etc.)

---

goal:

create a live, version-controlled, (semi) interactive repository of knowledge on:

-bash / terminal / shell

-linux / modern unix

-scripting

-anything that relates to *nix and terminal that is useful

------

-learn markdown

-learn github flavor of markdown

-decide how to approach the overall project meta (github markdown? obsidian but hosted on github somehow? some third thing?)

-mind-map the things you'll cover

-start writing!

------

i want:

-colors / syntax highlighting

-links / whole thing should be zettelkasten-like

-graded - i want to start off extremely simple, absolute basics, and take someone entirely through all the way to complex one-liners with fzf / expansion, etc.

-opinionated - make it the way you want, emphasize what *you* think is cool / useful!

-screenshots and / or gifs, screencasts from that one site, etc.

-whole thing should be searchable somehow right on github (via 'files' or something else, links, etc.)

------

my workflow:

-markdown / live preview

-vim typing / editing

-as standard in the markdown style as possible

-github actions / hooks as are useful

-live hosting for obsidian, of you go that route

-a way to publish releases, hide working branches, etc.

--------------------------------------------------------------------------------

general overview pattern for information:

reasoning - 'why' of linux, terminal, etc.

shell basics - globbing, cp, mv, etc.

editing with nano

interactive - fzf, etc.

vim, superior editing - modal-ize typing just like the shell modalizes *actions* we perform on a computer

------
