Pointers
==

# Pointer
A pointer is a variable storing memory address.
A normal variable holds a value, while pointer holds an address.

In this sense, a variable name directly references a value,
and a pointer indirectly references a value.

Referencing a value through a pointer is called indirection or dereference.

## Types
Similar to arrays, pointer are related to target types.
We say integer array or char array, but we can also say integer pointer or char pointer.

Side notes:  
We are talking about type here, so when a pointer points to nothing, its type won't change.
When a variable points to nothing, it means that the pointer's value is 0.

## Declaration
```c
char* p1;
int* p3;

char *p1, *p2;

// can mix with normal variables.
char *x, y, *z;

// x is the only pointer
char* x, y, z;
```

## Size
Since pointers are used to store memory addresses, pointers' size are the same on a specific machine.
We can use `sizeof` to see our machine pointer size (in bytes).
It could either be 4 or 8.

## Value
Pointers are for storing memory adresses.
These two are equivalent:  
```c
int n;
int *p = &n;

int *q = &n;
```

```c
int n;
int *p;
p = &n;

int *q
q = &n;
```

## Assignment
How about this?  
```c
int n = 3;
int *p = &n;
int *q = p;
*q = 5;
```
Here the value of the pointer `q` is the pointer to the address of `n`.
So when we assign a new value to the dereferenced pointer `q`, we are actually assigning the value of `n`.

So in general, `*p = value_of_target`.

Using `scanf`, we can assign a variable, one array element, or the assign a string.
Since the pointer already stores the address, we don't need to put an `&` in the `scanf` argument.

> ![note]
> Getting the address:  
>   `&variable`, `&array_name[index]`
> Dereference:  
>   `*pointer_name`

So for the definition `*` means the variable is a pointer (part of the definition),
but when using it again it means `*` dereferencing (unary operator).

# Pointer expression and arithmetic
Be careful when incrementing and decrementing pointers!
When it's an integer it's +4, and +8 with a double.

# `void` Pointer
When we define a pointer like so:  
```c
void* p;
```
It is not a pointer that points to nothing, it's a pointer to `void`.

It may hold adress like other pointers, we just cannot dereference.
This is because we don't know what size it is since it has no set size.
We can cast it to another pointer type to be able to dereference it.

Generally speaking, **void pointers to void are used as an adapter between pointers**.

# Pointer Vs. Array
Say we have:
```c
int data[10];
int * p = data;
```

We can do `p = p + 2;` but not `data = data + 2;`.
Remember, we cannot reassign an array.

# Char array vs char pointer

With char pointers, we can do:
```c
char *p = "hello";
p = "world";
```
but not
```c
p[2] = 'c';
*(p + 2) = 'c';
```

But with a char array `data`, we cannot do
```c
data = "world";
```
# Pass-by-val vs. pass-by-ref
We can use pointers as arguments if we want to change the original variable.
Here, we pass the value of the pointer (the address of its target) into the argument.
For example:
```c
int half(int* p) {
    *p /= 2; 
    return *p;
}
```

Since using pointers as arguments will enable to change the caller value.
If we don't have a plan to get value changed, we can add a `const` in front of pointers, e.g. `void read const(int* p);`

# Returning more than one value
One function can only return one value.
We can bring back more than one value using pointers.
```c
int max_min(int a, int b, int* p) {
    if (a > b) {
        *p = b;
        return a;
    }
    *p = a;
    return b;
}
```

# Array of Pointers
Examples:  

```c
int p[3]; /* an array of three integers */

int *p[3]; /* an array of three pointers to an integer */

int (*p)[3]; /* a pointer points to an array of three integers */
```

Step 1: Go inside the insidemost parentheses.
Step 2: find the variable name.
Step 3: Scan right.
Step 4: look at the type.
Step 5: Repeat for next outer parentheses.

# Pointer to Function
Functions in memory also always have a starting address.
We may use pointers to function.
All function names are addresses (similar as array names).

```c
#include <stdio.h>
int max(int a, int b) {...};
int min(int a, int b) {...};

int main(void) {
    int (*p_function)(int, int); // declare with function ptr
    p_function = max;
    printf("max is" ...);
    p_function = min;
    printf("min is" ...);

    return 0;
}
```
