Characters and Strings
==

# Fundamentals of strings and characters
A program may contain character constants.
A character constant is an int value represented as a character in single quotes.
The value of a character constant is the integer value of the character in the machine's character set.

```c
// don't forget the null character! '\0'
char a[0] = "hello";
char *p = "hello"; // this is not modifiable
```

Q: T/F? We cannot use char pointer to point to a string.  
A: False.

# String
A string is a series of characters btreated as a single unit.
A string may include letters, digits and various special characters.
String literals/constants in C are written in double quotation marks.

```c
char colour[] = "blue";
const char* colorPtr = "blue";
```

# Character-handling library (`<ctype.h>`)
`<ctype.h>` includes several functions that perform useful tests and manipulations of character data.
Each function receives a character, represented as an `int` or `EOF` as an argument.
Some functions include:
1. `isdigit`
2. `isnum`
3. `isalnum`
4. `isxdigit` for hexadecimals
5. etc.

# String Conversion  
> ![tip]
> MIDTERM:  
> There will be questions where you cannot use any pre-defined functions.
> Clearly indicate which header file you need to add.

`<stdlib.h>` is the general utilities library.
It offers char pointer to other data types.
Throws `RuntimeError` if the input data does not match the required datatype.

# More on `<stdio.h>`
We have `sprintf` and `sscanf` which prints and scans to a char pointer.
`fgets` inputs characters from the specified stream into an array until `EOF` is encountered or `n` bytes are read.

> ![note]
> stdio vs. stderr?
> conventional output vs. standard output

When you write an integer to an array it takes four bytes no matter how long it is.
When you write a string to a char array it only takes one byte per character since it's a string.

# String Manipulation
`<string.h>` provides many useful functions for manipulating string data (copy and concatenate), comparing.
So in exams add `<string.h>` when using `strcmp`, `strlen`, etc.

Every function appends `\0` except for `strncpy`

`strcpy` copies the entire string array to a variable while `strncpy` copies the first `n` characters into another array.
strcat appends the second argument into the first (a character array), the first character of the second argument replaces `\0` that terminates the strin gin the first argument.

`strcmp` Compares two strings. can return 0, +1, -1.
When using `strncmp`, we see the difference between the ascii values.

# Search functions of `<string.h>`
`strstr` searches for the first occurence of the string in another string.

`strtok` this function is used to break a string into a series of tokens.
Apparently it does not fully depend on the input.
This is because it stores that data that it has between calls.

```c
while (tokenPtr != NULL) {
    ...
    tokenPtr = strtok(NULL, " ");
}
```

# Memory Functions of the String-Handling Library
`memcpy` copies n characters from one object to another.
The number you put in the `memcpy` is the number of bytes.
In `memcmp` we also use bytes.

`memset` copies the vlue of the byte in its second argument into th efirst `n` bytes of the object  pointed to by its first argument,
where `n` is specified by the third argument.

# Other Functions
`strlen` calculates the length of the string (except for the `\0`), but it is not encouraged to do so.


