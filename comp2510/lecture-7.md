`qsort()`
==

# Sorting algo qsort
`qsort` is found in `stdlib`, with signature
```c
void qsort(void* base, size_t n_items, size_t element_size, int (*compar)(const void*, const void*))
```

Take note of the last parameter.
It is a pointer to a function that returns an `int` and a pair of `const void*`.

Example:
```c
#include <stdio.h>
#include <stdlib.h>

int mysort(const void* a, const void* b) {
    // cast
    int* p = a;
    int* q = b;
    // dereference
    return *p - *q;
}

int main() {
    int data[5] = {2, 0, 5, 3, 9}; 
    qsort(data, 5, sizeof(int), mysort);
    printf("%d %d %d %d %d", ...);
    return 0;
}
```

If `n_items` is larger than the actual array size, it will be a logic error/undefined behaviour.

# Sorting Pointer Arrays
```c
int mysort(const void* a, const void *b) {
    // cast to a pointer of int pointers
    int** p = (int**) a;
    int** q = (int**) b;
    
    // dereference twice to get to the actual int values
    return **p - **q;
}
```

For `char*`, 
```c
int mysort(const void* a, const void *b) {
    // cast to a pointer of int pointers
    char** p = (char**) a;
    char** q = (char**) b;
    
    return strcmp(*p, *q);
}
```
For comparator, we use the difference between compare.

It's going to be a more complicated comparator if we
want to compare with more than one conditions.
