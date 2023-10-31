# EIAF ("everything is a file")

In UNIX (with certain exceptions), *"everything is a file"*; that is to say, all essential aspects of the high-level operating system are controlled by files, whether we're writing to a stream, configuring a command, etc. This pattern / convention afford many benefits. We can:

- almost always [pipe](pipes.md) the output of one command to another as input, facilitating easy, powerful [command chaining](command-chaining.md).
- solve most routine problems on the command line with a *textual* approach, text wrangling, etc.
- easily write the results of any command (or chain of commands) to an output text file with [redirection](redirection.md).

In short, this makes it relatively trivial to manage complex command-line operations and manage the output. This all ties in to the *Unix Philosophy*[^1].

[^1]: https://en.wikipedia.org/wiki/Unix_philosophy