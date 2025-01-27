Functions
==

# Program modules in C
> ![note]
> No global variables!

The best way to develop and maintain a large program is to construct it from smaller pieces or modules,
each of which is more manageable than the original program.
Modules in C are called functions.

There are two types of functions:
1. Predefined functions
2. Programmer-defined functions

## Template
```c
return_value_type function_name( parameter_list ) {
    // function body/block
    definitions
    statements
}
```

# Functions
If you declare the function, you can use any name for the parameters.
Minimally, you can write the signature.
For example,
```c
void f1(int y, int x);
void f1(int, int);
void f1(int a, int b);

// definition
void f1(int x, int y) {
    ...
}
```
What's important is the type of the parameters.

## Functions with or without return value
There are three ways to return control from a called function to the point at which a function is invoked.
1. let the function reach the ending brace
2. `return;`
3. `return expression;`

If you use the third return for a function with a `void` return type, the compiler will throw a syntax error.

## Invocation
Invoking a function is the same thing as calling a function.
Functions are invoked by a function call, which specifies the function name and provides information (as arguments)
that the funciton needs to perform its designated task.

> [!note]
> Nested function definitions do not exist in C

In one function definition, there can be more than one `return` statements.
But logically, the statement will only be run once as `return` is an exit from the function.
Function return value can also be used as an argument of another function.

If you forget to return a value for a function that is not `void`, it can lead to unexpected errors.
The `C` standard states that the result of this ommission is *undefined*.

Compiler warnings for narrowing conversions.

> [!note]
> Conversion spec for `double` is `%f` for `printf` and `%lf` for `scanf`.``

# Math library

Simple absolute value function:
```c
int abs(int val) {
    return val >= 0 ? val : -val;
}
```

Math library `math.h` is a predefined header file.
It contains functions related to math.

# Headers
To get access to predefined functions, we use `#include` at the start of the file.
The compiler then pastes the contents of the `.h` file into the `.c` file.
The compiler also automatically searches a header file with the same name as your C file
to search for the function prototypes/declarations.

# Random Number Generation (RNG)
RNG is included in `stdlib.h`.
We can use RNG with `int rand();` which returns an integer between `0` and `RAND_MAX = 37267`.

In general, to obtain a value from `min` to `max` inclusive:
```c
i = rand() % (max_value - min_value + 1) + min_value
```
In the backend, C has a list of numbers to give `rand` a random.
This makes C deterministic by default.
To make it more random, we use `crand(seed)` to assign a seed to
the randomiser.
We can leverage the system time with `time(NULL)` to assign a random seed.
Take note that `time()` is in `time.h`

# By value vs By reference
All function calls are by value.
That means a copy of the argument's value is made and passed to the function.
We can simulate passing by reference though, using pointers or address.

Pass/call-by-value is used whenever the function does not need to modify the value of the caller's original variable.
This prevents accidental side effects that so greatly hinder the development of correct and reliable software systems.

# Scope rules and storage classes
A file and each pair of curly brackets `{}` defines a scope.
Your variables are only alive/accessible in the scope in which they are defined.

## Storage classes
Attributes of variables include name type size and value, as well as storage class, storage duration, scope and linkage.
C provides four: `auto`, `register`, `extern`, and `static`. 
This is talking about the lifespan of the variable.

# Recursion
A function that calls itself directly or indirectly with different arguments.
Each function should have at least one base case to stop.
It can call itself more than once.


