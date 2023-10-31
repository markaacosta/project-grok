# IFS

The `IFS`, or *internal field separator*, is a shell variable that controls how the shell splits [words](words.md). 

By default, the value of `IFS` is `"\ \t\n"`; in other words, spaces, tabs, *and* newlines are treated as word boundaries. Sometimes, we may wish to be more restrictive; for instance, changing the `IFS` to *only* be the newline character as one of several strategies for managing files with odd characters in their names, like spaces.

## temporarily changing the IFS for a while loop construct

```bash
while IFS=$'\n' read -r line; do
  echo "$line"
done < input_file.txt
```

> a construct like this (or within a function, for instance) allows for an easy, temporary change to the IFS.

## capturing the default IFS to restore it later

A fairly common convention is to *retain* the IFS variable value, then restore it after some operation(s):

```bash
OLD_IFS=$IFS

#CHANGE
IFS=$'\n'

#perform some operations...
#then...

#RESTORE

IFS=$OLD_IFS
```