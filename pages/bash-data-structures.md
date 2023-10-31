# Bash Data Structures

Some basic array information follows; for more comprehensive information, and / or information about associative (key-value) arrays, consult the bash manual[^1].

[^1]: https://www.gnu.org/software/bash/manual/bash.html#Arrays

## Bash Arrays

### Create

> create an (empty) array

`declare -a my_array`

### Create (and fill)

> create an array, and fill it with some initial values

`my_array=(one two three)`

### Access a certain value

> access the second value from the above example

`echo ${my_array[1]}`

### Add a value at a given index

> add value at index '5'

`my_array[5]="some value"`

### Extend array

> fill the array with multiple new values (at next available indices)

`my_array+=(another few values)`

### Print entire array contents

> print array elements to `stdout`

`echo ${my_array[@]}`

### Print array length / num elements

> print number of array elements to `stdout`

`echo ${#my_array[@]}`

### Loop / iterate an array

`my_array=(arrays are fun); for item in ${my_array[@]}; do echo "$item"; done`

or, more readably:

```bash
my_array=(arrays are fun)
for item in ${my_array[@]}; do
  echo "$item"
done
```

![for-array-element](../assets/for-array-element.gif)

## Bash Associative Arrays (Dictionaries)

Bash also has *associative arrays*: arrays of *key-value pairs* rather than just values. Examples below show where syntax *differs* from standard bash arrays:

### Create

> create an (empty) array - notice that for assocative arrays, the flag is capitalized (`-A`)

`declare -A my_array`

### Fill Associative Array

> fill associative array with some values (notice that *keys* are defined wrapped in square brackets, while values are wrapped in quotes)

`my_array=([one]="bash" [two]="is" [three]="fun")`

### Access a certain value

> from the above example, access the value that corresponds to a certain key. Notice the key is not wrapped in quotes.

`echo ${my_array[one]}`

### Print entire array contents

> print array elements to `stdout`

`echo ${my_array[@]}`

### Print array length / num elements

> print number of array elements to `stdout`

`echo ${#my_array[@]}`

### Loop / iterate an array

`for i in "${!my_array[@]}"; do echo "key : $i"; echo "value: ${my_array[$i]}"; done`

or, more readably:

```bash
for i in "${!my_array[@]}"
do
  echo "key : $i"
  echo "value: ${my_array[$i]}"
done

```

![for-associative-array-key-and-value](../assets/for-associative-array-key-and-value.gif)
