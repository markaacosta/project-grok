# Tmux / Multiplexers

When using terminals, it's common to need more than one shell instance at a time. In a GUI and / or local machine, we can simply open up another GUI instance of the terminal. Some terminals also supports opening multiple tabs in the same window. However, not all terminal emulators support tabs; among those that do, the key bindings will be different, etc. Furthermore, work working, a GUI / multiple terminal shells may not be available.

Regardless of whether we're working remotely or locally, we can address all these points and simplify / harmonize the way we work with a <mark>terminal multiplexer</mark>. A *terminal multiplexer* allows for multiple shells / tabs / even tab arrangements within a single terminal emulator instance. Some terminal multiplexers:

- tmux
- screen
- zellij

In this page, we'll be focusing on `tmux`. Concepts should apply fairly well to other multiplexers.

## tmux

With tmux installed, we can run `tmux new` to create a new session. 

### prefix

In tmux (and other applications which rely on keyboard shortcuts), often, there is a preliminary shortcut that we always type before typing the main shortcut we wish to execute. This is called different things in different programs; in tmux, it's called the `prefix`. The prefix can be changed; in tmux, by default, it is \<ctrl-b\>. We'll always refer to this shortcut as `prefix` from here onward.

Once in tmux, run this command to familiarize with the tmux shortcuts used to perform actions:

`prefix` + `?`

### tmux workflow - shortcuts vs. commands

As with many programs, a user can interact with tmux either through keystrokes, or commands. Learning keystrokes is faster; if you wish to enter commands, type:

`prefix` + `:`

then type the command to run

### interactive demos

#### prefix deviation

> you'll notice my prefix (shown in the demos) is \<ctrl-k\> rather than \<ctrl-b\>; bear this in mind when observing the demos.

#### create new window

![asdf](../assets/try.mp4)

#### kill window



#### create vertical split



#### create horizontal split



#### switch window / page (interactively)



#### switch window (by index)

