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

```c
void free(void* ptr);
```
This releases the memory block.  
`ptr` is the pointer to a memory block that was dynamically allocated before.  
Its an alias for the `realloc` with size 0.

> [!note]
> `free` does not need size.

## forgetting to free
We will get memory leaks.
Should definitely avoid this.

Counterparts:  
| C | C++ |
|---|-----|
|malloc() | new |
|calloc() | |
|realloc()| |
|---------|--|
|free() | delete |
|       | delete[] | 

# Dynamic Data Structures
Dynamic data structures have sizes that grow and shrink at execution time.

## self-referential structures
This is when a structure contains a pointer member that
pointer to a structure of the same structure type.

When we talk about arrays or linked lists, they are (physical) data structures.
Implementation is concrete.
Queue and Stack are logical data structures, they can be implemented
with either arrays or linked lists.
Queue and Stack are behavioural properties instead of physical.

## standard idiom for linked list traversal
```c
node* p;
for (p = head; p != 0; p=p->next) {
    /* process p->data */
}
```

## destroying a linked list
If we use the standard idiom, we will cause a nullpointer.
To resolve this, we can use another auxiliary node to
hold the next node temporarily.

```c
void destroy(node* head) {
    node p*, q*;
    for (p = head; p != 0; p = q) {
        q = p->next;
        free(p);
    }
}
```

## insertion of data into a linked list
We have 3 different ways to insert:
1. at beginning
```c
int insert_front(node** phead, int data) {
    node* newNode = malloc(sizeof(node));
    if (newNode == 0) {
        return 0;
    }
    // assign values
    newNode->data = data;
    newNode->next = *phead;
    // update head
    *phead = newNode;

    return 1;
}
```
2. in sorted order

    We need to find the correct location,
    and we need to traverse the list to compare data
    (with handler of the previous node).
    So then, we need to keep track of the 
    address of the previous node's `next` (`**`).

```c
// example (descending)

int insert_desc(node** phead, int value) {
    node** tracer;
    node*  newNode = malloc(sizeof(node));

    if (newNode == NULL) {
        return 0;
    }
    newNode->data = value;

    for (tracer = &head;  *tracer != 0; tracer = &(*tracer)->next) {
        /* try to insert or remove node */
        if ((*tracer)->data <= value) {
            break;
        }
    }

    newNode-> next = *tracer;
    *tracer = newNode;
    return 1;
}
```

3. at end (see lab)

