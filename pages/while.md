# Bash `while` loop

Like most programming / scripting languages, bash has a `while` looping construct; check the bash manual for full details [^1]

[^1]: https://www.gnu.org/software/bash/manual/bash.html#index-while

## `while` loop examples

examples of common ways a `while` loop might be used in practice:

### while *read lines from text file*

> whenever reading lines from a text file, prefer a `while` to a `for` loop; the former is more robust for reading lines of a text file

`echo -e "this\nis\nfun" > file.txt; while read -r line; do echo "$line"; done < file.txt`

or, more readably:

```bash
echo -e "this\nis\nfun" > file.txt

while read -r line; do
  echo "$line"
done < file.txt
```

![while-read-lines-from-text-file](../assets/while-read-lines-from-text-file.gif)