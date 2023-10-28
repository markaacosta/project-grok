# Process Substitution

Some commands take files as arguments; for such commands, if we have output on the command line that we want to pass as an argument, we can run the command, [redirect](redirection.md) its output to a text file, and use said text file; still, this can be tedious.

With *process substitution*, we can treat the output of a command as a file without ever having to actually write it to file; if we want to compare the content of a *file* with the content of a *command*, we can do that:

![process-substitution](../assets/process-substitution.gif)

> process subtitution is a very useful pattern for treating standard command output as a file