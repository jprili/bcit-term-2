Formatted I/O
==

# Streams
Everything is transferred to I/O character by character.
Errors are sent to the `stderr`, by default is connected to the screen.

All I/O is performed with streams, which is a sequence of bytes.

## Conversion Specifiers
Remember: `d` and `i` are different!
Also `x` prints the letters in lowercase, and `X` in uppercase.

In C, `int`s are stored in two's complement.

For floats, `e` and `E` are for scientific notation, and `f` for fixed point.
`g`/`G` if we want to express the float as `e` or `f`.
`L` to show a float double.

> ![tip]
> In midterm, things in short answer can be impossible.

`n` stores the number of characters into an `int` pointer.
It does not print anything, just stores the value.
Also, we can store the number of characters printed by assigning `printf` to an `int` variable.

# Printing Width
The exact size of a field in which data is printed is specified by a field width.
`"%4d"` sets the printing width of the input integer, effectively right aligning, negative would align left.
Adding a `+` before the `int` indicates an explicit `+` symbol for positive values.
Mind that the negative sign counts as a character.

For `int`, `"%.4d"` determines how many leading zeroes to pad the `int` to the left when applicable.
We can also use it for strings, indicating the number of characters to displays at most.

For non-base-10 integers, we can use `#` to add the leading character `0` for octal and `0x` for hex.

# more scanf
Scan set `[]` only scans characters in between `[]`
Good practice is to use `sscanf` with the set after using `scanf` to a string.

# `main`
If we want to run the code with parameters, we can use
```c
int main(int argc, char* argv[]) {
}
```
In java, the compiler doesn't count the program name, while it does in C.
