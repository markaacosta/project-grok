# Words / Shell Tokens

In shell terminology, a <mark>word</mark> (or 'token') is a piece of what you type, separate from other pieces. For instance, when you type and run some command:

`find * -type f -iname "*.pdf"`

...the shell has to figure out what parts are a *command* (`find`), an *option* (`-type` or `-iname`), an *argument* ("*.pdf"), and so on.

Gaining an intuition for how the shell interprets different `words` is an important part of understanding how to write commands. This comes down to paying attention to paying attention to the different parts of what is written on the command line, much like the parts of speech in language.

Learn more about the particulars of words by reading the definition of a *word* in the bash manual, and looking elsewhere in the manual for instances of the word "word"[^1]

[^1]: <https://www.gnu.org/software/bash/manual/bash.html#index-word>
