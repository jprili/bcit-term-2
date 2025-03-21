DMA and Data Structures
===

# Dynamic Memory Allocation
Review: `void*` cannot be referenced directly,
they are still pointers; they can only be dereferenced after a case.
As a type, a void pointer can be used as a parameter or return type.

Review: `size_t` is an unsigned integer type which can assign only values >= 0 integer
values. It is used on object sizes and returned by `sizeof`.
`const` is the syntax representation of `size_t`, but you can still 
run the program without.

> [!warning]
> `sizeof` is an operator!

## functions
```c
void* malloc(size_t size);
```
`malloc` stands for memory allocation.  
`size` is in bytes.

This will return either a pointer to the allocated memory,
or `NULL`.


```c
void* calloc(size_t n_items, size_t size);
```
the `c` in `calloc` stands for "clear".  
`n_items` is the number of elements.  
`size` is the size of each element.

This will return either a pointer to the allocated memory,
or `NULL`.

```c
void* realloc(void* ptr, size_t size);
```
This is for reallocation.
It will allocate a new block somewhere else, and copy over all the data from the old block.  
`ptr` is the pointer to the memory block previously allocated with `malloc`, `calloc`, `realloc`.  
`size` is the new size of the memory block.

This will return either a pointer to the allocated memory,
or `NULL`.


