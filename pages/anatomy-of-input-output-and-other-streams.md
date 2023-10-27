# Anatomy of Input, Output, and Error Streams

<mark>Streams</mark> are an essential part of the command line. For instance:

![basic-stream](../assets/basic-stream.gif)

In the above example, "this", "that", and "one more thing" were printed to the terminal. This means they are *output*, and thus part of the standard *output* stream. There are three standard streams:

- `stdin`: the *standard input* stream
- `stdout`: the *standard output* stream
- `stderr`: the *standard error* stream

## stdin

With *standard input*, a command receives text ('input') *from* something. For instance, the `cat` command could receive input *from* a text file and print it to the screen:

![stdin-basic](../assets/stdin-basic.gif)

## stdout

With *standard output*, a command sends text ('output') *to* something. For instance, the `echo` command seen above prints its argument to the screen on standard output:

![stdout-basic](../assets/stdout-basic.gif)

## stderr

With *standard error*, a command sends error-related messaging ('errors') *to* something. For instance, trying to use a non-existent command will cause an error message to be written to the terminal (it is visually indistinguishable from standard output):

![stderr-basic](../assets/stderr-basic.gif)

## Tao of Streams

Streams are so important because everything we do on the command line is either read from input, send to output (on the screen), or sent to error (on the screen). No matter how complicated the commands we write may be, they are a negotiation between the streams.

## Piping - Stream Continuation

Now that you understand streams, you are prepared to understand [pipes](../pages/pipes.md), which allow for the chaining of streams in a continual `input->output ------> input->output` pattern.

## Redirection

Above, we saw the way the different streams work by default; [redirection](../pages/redirection.md) is how we change the behavior / destination of streams on the fly.