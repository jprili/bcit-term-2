Structures
==

Also called aggregates.
They are collections of related variables under one name.

# Structures
Structures are derived data types -- they are constructed using objects of oher types.
The identifier card is the structure...

Example:
```c
struct score {
    car id[10];
    int score;
};
```
Variables declared within the braces are the members.

A struct cannot contain an instance of itself.
This is because calculating the size will have an infinite
recursion.
Use pointers instead.

How many instances of `struct card` here?  
A: 53
```c
struct card aCard, deck[52], *cardPtr;
```

# Initialising a structure
```c
struct card aCard = {"Three", "Hearts"};
```

# dot vs arrow
Dot is for struct instance, while arrow is for pointer of struct.

# Copying all members
```c
s[1] = s[0]
```

Remember: `sizeof()` is an operator.
In general `sizeof(structure)` >= sum of sizes of its members.
Since the compiler is allowed to add paddings between members at the end of a structure
due to alignment of requirements.

# typedef
```c
typedef struct {
    char* face;
    char* suit;
} Card;
```

Example:
```c
struct Address add1;
typedef sstruct Address address;
address a, addresses[10], *p;
```

```c
typedef int[25] numbers; // wrong
typedef int numbers[25]; // correct
```

# Union
A derived data type with members that share the same storage space.
For different situations in a program, some variables
may not be relevant, but other variables are.

```c
union number {
    int x;
    double y;
};
```
The operations that can be performed on a union are the following:
* Assigning a union to another union of the same type.
* Taking address of union variable
* dot and arrow.

We cannot compare unions with `==` or
`!=` for the same structures cannot be compared.

# Bitwise operations
* AND (&)
* OR (|)
* XOR (^)
* left shift (<<)
* right shift (>>)
* complement (unary)

# left and right shift
left shift will always add zero at the rightmost digit  
right shift will add the same number on the leftmost.

# Bit fields
```c
struct bitCard {
    unsigned face   : 4;
    unsigned suit   : 2;
    unsigned colour : 1;
}; // <= 32 bits
```

# Enum
Enumeration constants.
Values in an `enum` start with zero and incrementing by 1.

```c
enum months {
    JAN = 1,
    FEB,
    MAR,
    ...
};
```
