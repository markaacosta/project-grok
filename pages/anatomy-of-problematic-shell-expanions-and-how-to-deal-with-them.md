# Handling Problematic Shell Expansions

## When Possible, Avoid Problems In the First Place

Adhere strictly to good patterns and habits when creating directories ([directory hygiene](../pages/directory-tree-hygiene.md)) and files ([filename hygiene](../pages/filename-hygiene.md))

## Spaces - Both Characters and Word Separators

Whenever filenames have spaces, wrap them in double-quotes like so:

`some file.txt -> "some file.txt"`

This will handle many common expansion problems.

for more information and a practical example see [this case](xargs.md#strategy-1---double-quote-for-proper-expansions)

## Special Characters

In more complex cases with other symbolic characters, a more robust solution is to use nul-terminated sequences. These are invisible characters, but many common tools have a flag that allows their use (check the manual for a given tool). On-the-fly, `tr` can also be used for new-line to nul conversions:

`{somecmd} | tr '\n' '\0'`

for more information and a practical example see [this case](xargs.md#strategy-2---nul-terminated-sequences)

## Escape Sequences / When to Escape

TODO