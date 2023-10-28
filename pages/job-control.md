# Job Control

Operations undertaken in bash can be considered *jobs*; on modern computers, and / or with simple commands, jobs can run very quickly. Other jobs may be slower. All jobs can be managed for the duration their commands run, and this is *job control*.

## Run a command, suspend it, and resume it

Once a command is running, we suspend it with the keybind `^c-z` (ctrl-z)

> run command

`sleep 100 && echo "done"`

> suspend it

`<ctrl-z>`

> list (current) jobs

`jobs`

> bring job back to *foreground* (i.e. resume running the command)

`fg %n`, where `n` is the number associated with the job when we ran the `jobs` command

<mark>all the above in action...</mark>

`sleep 100 && echo "done"`

![job-main-actions](../assets/job-main-actions.gif)

## Immediately send a job to the background

A job can be sent to the background at the same time that you invoke it (unlike above, in this case, the command *will* already be running in the background despite not being visible in the terminal)

`sleep 100 && echo "done" &`

> the only difference is we type an `&` at the end of the command

<mark>the above in action...</mark>

![job-bg-immediately](../assets/job-bg-immediately.gif)

## Kill a background job

`kill %n`, where `n` is the number associated with a given job

![job-kill](../assets/job-kill.gif)

## Disown a process

Some GUI processes depend on the terminal from which you open them; closing the terminal also kills the GUI apps. In this situation, you can <mark>disown</mark> a process so becomes 'detached' from the terminal and runs with its own process. For example:

`nautilus . & disown`

> open a nautilus instance in the current directory but use *disown* to 'detach' the process from the terminal