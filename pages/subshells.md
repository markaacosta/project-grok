# Subshells

When one or more commands are placed between parentheses, this constitutes a <mark>subshell</mark>. A *subshell* executes itself before the normal shell scope. Often, rather than just execute the subshell first, we want to also capture its output to use in the main shell context - this is called [command substitution](expansions.md#command-substitution).