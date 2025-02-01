Arrays 
==

# Arrays
Logically, arrays are data structures consisting of related data items of the same type.
Physically, they are groups of memory locations related by the fact that they all have the same name and type.

In C, we only have arrays, no `ArrayList`, unlike Java.
Since arrays are just some consecutive memory cells in C, arrays do not know their length.
In C, array length can NOT be changed (when we need to resize, we need to efine a new array, and then copy over existing data).

We can define a new array with 
```c
int arr[10]; // we cannot reassign the variable anymore!
arr = ... // compile error if we do something like this
```
The array is bound to `arr` itself.

## Out of bounds
C doesn't provide any specification which deal with prolem of accessing invalid index.
As per ISO standard, this is called *Undefined Behaviour*.

## more ways to define
```c
int c[12]; // note: contents cannot be assumed to be 0
int b[100], x[27];

// initialisation
int a[3] = {1, 2, 3};
int y[13] = {1, 2, 3}; // rest will be 0
int v[] = {1, 2, 3, 4, 5}

// initialise a 100-size array with 0 
int t[100] = {0};

// not allowed !!!
int w[3];
w = {1, 2, 3}; // renaming the variable is not allowed
// w already bound to the starting address of w

// not allowed !!! (compile error)
int u[3] = {1, 2, 3, 4, 5};
```

When we define an array, the given size/length must be constant.

> ![note]
> `const` and `#define` have different scopes.

## Out of Bounds II
Reading may lead to returning unexpected data, while setting will lead to a segfault.

# Looping an array
The standard idiom to process an array is:
```c
T arr[N];
size_t i;
for (i = 0; i < N; i++) {
    /* refer to each element with arr[i] */
}
```

Notes:
1. `T` is a type
2. `N` is the array length > 0
3. `size_t` is a type for storing sizes (some unsigned `int`)

From now on, we use `size_t` for our loop counters;

```c
void function1(const int arr[], size_t n) {
    ...
}

void function2(const double arr[], size_t n) {
    ...
}
```

`const` is added so that we ensure that arr[] is not changed.

# `char` Arrays
We can define `char` arrays with
```c
char buf[10] = "";
// equivalent to
char buf[10] = {0, 0, 0};

char buf[3] = " ";
// equivalent to
char buf[3] = {' ', 0, 0};

char buf[3] = "a";
// equivalent to
char buf[3] = {'a', 0, 0};
```

We can also use `\0` to indicate the end of the string literal in the array definition.
```c
char buf[3] = {'h', 'i', '\0'};
```

## for strings
`"%s"` for reading in and printing out a string with a a `char` array.
```c
char word[100];
scanf("%s", &word[0]);
// or shorter
scanf("%s", word);
printf("%s", word); // only time where you give it an address

// if we want to start from index 10
scanf("%s", &word[10]);
scanf("%s", word + 10);
```

## looping through a char array to store a string.
```c
char s[] = "hello";
size_t i;
for (i = 0; s[i] != '\0'; i++) {
    /* refer to each char with s[i] */
}
```

# Passing arrays to functions
Non-string arrays should have its length also passed.
String arrays don't need it since there is a `\0` at the end.
`a === &a[0]`

# Sorting Arrays
Often, the simplest alorithms perfom poorly.
Their virtue is that they are easy to write, test and debug.
More complex algorithms are often needed to realise maximum perfmance.

# Bubble/Sinking sort
The smaller values gradually "bubble" their way upward to the top of the array like air bubbles.
We still make several passes through the array.

```c
#include <stdio.h>
#define SIZE 10

inf main(void) {
    size_t pass, i;
    int arr[SIZE] = ...;
    for (pass = 1; pass < SIZE; pass++) {
        for (i = 0; i < SIZE - 1; i++) {
            if (a[i] > a[i + 1]) {
                hold = a[i];
                a[i] = a[i + 1];
                a[i + 1] = hold;
            }
        }
    }
    ...
    return 0
}
```

# Multidimensional Arrays
You can have arrays of arrays as well.
Its elements can be accessed with `a[i][j]`.
It can also be initialised with
```c
int arr1[2][3] = {{1, 2, 3}, {4, 5, 6}};
int arr2[2][3] = {1, 2, 3, 4, 5};
int arr3[2][3] = {{1, 2}, {4}};
```

When passing an $n$-dimensional array, all other values must have length except for the first one.
Apparently it is included in the type and it is not known at compile time.
For example:
```c
# define EXAMS 4
void printArray(const int grades [EXAMS], int pupils, int tests);
```
