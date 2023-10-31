# `fpp`

Like [fzf](fzf.md), `fpp` is a fuzzy picker. `fzf` is a general-purpose tool; `fpp` is a tool (from *Meta*, and used internally in the company) for a specific scenario; in this scenario, we expect a large amount of output on `stdout`. Some of this output is filepaths; potentially, much of it is not. In this particular scenario, `fpp` is uniquely suited to the task at hand. fpp will look at all this and, using granular regex, identify likely candidates for filepaths. fpp will then let us pick from them, and, if needed, so something with the results.

The example from Meta's repo itself is more than adequate to demonstrate its basic utility:

[![asciicast](https://asciinema.org/a/19519.svg)](https://asciinema.org/a/19519)