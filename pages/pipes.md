# Pipes / Piping

`|`

The above character is a *pipe*. A pipe construct looks like this:

`echo -n "cool" | wc --chars`

This command will produce the output `4` - the number of characters in the word 'cool'. How does it work. Let's understand the parts first, then put it together.

## Part 1 - The `echo` command

`echo "cool"`

> Notice we are leaving the `-n` flag out for now; we'll come back to that later. In any case, this will print the word "cool" to the *screen*:

![pipe-part-1](../assets/pipe-part-1.gif)

## Part 2 - Understanding `wc`

`wc -l < many_lines.txt`

> `wc` can count bytes, characters, words, or lines in a file, or *input stream*. We could see how many lines are in a big file (notice we pass the `-l` flag so `wc` knows it's the number of *lines* that we want to count):

![pipe-part-2](../assets/pipe-part-2.gif)

## Part 3 - Putting It Together

`echo "cool" | wc --chars`

> This is where the magic happens. Notice below that the word "cool" does *not* get printed to the screen on standard output like you might think. Instead, the *output* of the `echo` command becomes *input* for the next command, which is `wc` in this case. This is <mark>piping</mark> - when we have one (or more) sets of commands separated by pipes, and those pipes take whatever is on their left and pass it as input to whatever is on their right.

![pipe-part-3](../assets/pipe-part-3.gif)

> Still, something is wrong; we expect `4` and get `5`. Why? Let's explore below:

## Part 4 - A Small Fix

`echo -n "cool" | wc --chars`

> By default, the `echo` command prints a <mark>newline</mark> at the end of what we ask it to print. This is an invisible character that literally puts a "new line" on the terminal so our prompt appears where we expect it to, so we can handle other situations that need each piece of output to be on its own line, etc. This newline character is counted, and we don't want this, so we suppress this with `-n` flag. This causes the expected output to be produced: 

![pipe-part-4](../assets/pipe-part-4.gif)