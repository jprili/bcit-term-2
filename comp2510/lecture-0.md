Procedural Programming -- COMP 2510
==

# Running code
In C, running a code actually involves two things:
compiling and running the code.
We can take the `.c` and `.h` files to generate binary in `.o` format.

> [!warning]
> Labs due by noon of following Friday!
> Dropbox is closed by 1:30 on Friday.

# Your First Program 
```c
#include <stdio.h> // standard i/o

int main() {
    printf("Hello World");

    return 0;
}
```

> [!note]
> When asked with "write a program",
> write everything needed for the c file.
> This includes the headers (`.h`) files
> and `main()`.

The `main()` function must be there for the compiler.
Possible signatures are:
```c
int main() {}
int main(void) {} // no intentioned arguments
int main (char* argv, int argc) {}
```

If the function does not return anything, specify with void.
If you miss that, the compiler would throw a `CompilerError`.
`RuntimeError` would happen if even the syntax is correct, there is some unforeseen logic that the computer *cannot* do.

# Main return values
`0` is success.
Anything less than is a fail.

Like in Java, indentation does not matter, and it is only there for readability.
Use semicolons to end a statement.

# Program structure
1. `#include`
2. `int main()`
    * statements
3. ` function b()`
    * statements

Functions are the building blocks of C.
There are five types of statements:
* declaration
* assignment
* function
* control
* null

The main function is the first function calle, but it does not need to be the first function in the code.
Pay attention on the differerence between defining, calling, and declaring a function.


```c
#include <stdio.h> // standard i/o
// the line above will be replaced by stdio contents

int main() { // function definition
    printf("Hello World"); // print statement

    return 0;  // return statement
}
```

# Takeaways
1. Statements can be inside or outside of functions. Industry standards does not like it.
2. Functions can only be outside of another function.
3. In C, there is **NO** boolean type of data. Developers still use `int` to express boolean.
    * `_Bool` introduced in C99.
    * Non-zero is true, false otherwise.

# Declaration
To declare a function,
```c
returnType functionName(ParameterList);
```
For variables,
```c
varType varName;
```
This is so that the compiler knows what type the variable has, 
and which scope level it's in.

# Data Types
* `char`
* `int`
* `long`
* `float`
* `double`

We also have arrays and pointers.

# Assignment
We use assignments to give value to a variable.
We can also increment (`++`) or decrement (`--`) a value.
We can chain assignments as well.
```c
height = length = width = 10;
```
C also has compound assignment as well.

> [!note]
> If the `++` is before the variable, increment first
> otherwise, increment after.

# Function Call
1. `printf("hello world")`
2. `scanf("%d", &num)`
3. `my_function`
4. `int num = scanf("%d", &num)`

You cannot call a function that isn't declared yet.
We can either move the function before it is called, or declare it before the function.

> [!note]
> Q: If we can move things around, why use declaration?  
> A: Take a mutually recursive program, you cannot call `b()` from `a()` and `a()` from `b()` at the same time.

# Null Statement
Denoted by a `;`.

# Basic Print Statements
Before printing anything, make sure `#include <stdio.h>` is in the beginning of the file.
1. One line print: `printf("hello world");`
2. Multiple lines: `printf("hello\n world");`
3. Print a number: `int num = 10; printf("This number is %d", num);`
4. Print a char: `char one_char = 'a'; printf("This number is %c", one_char)`

If you have more than one main function in the project, the program will throw a `CompilerError`, if you have no main function `RuntimeError`.

## Escape Sequences
|\n | newline |
|\t | tab |
|\a | alert. sound the system bell |
| \\ | backslash |
| \" | double quote |

# Basic `scanf` statements
```c
// read in one number:
int num;
scanf("%d", &num);

// multiple numbers
int num_1, num_2;
scanf("%d %d", num_1, num_2);

// char
char one_char;
scanf("%c", &one_char);

```
`&` means takes the address of the variable.

# `if` Statement
Syntax:
```c
if (condition)
    one_statement;

if (condition) { // recommended
    several_statements;
}
```

## `if-else`
```c
if (condition) {

} else if () {

}
```

## `if-else` ternary operator
Use case 1: statements  
```c
grade >= 60? printf("Passed\n") : printf("Failed\n");
```

Use case 2: values  
```c
printf("%s\n", grade >= 60 ? "Passed" : "Failed");
```
In the above example, the value of the ternary operator is the address of `"Passed"` or `"Failed"`.


