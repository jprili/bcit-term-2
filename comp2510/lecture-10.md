Other Topics
==

## Variable Length Argument List
We use the ellipsis to define variable arguments of any type.
It needs to be at the end of the parameter list.

```c
printf(const char* format, ...);
```

### `<stdarg.h>`

```c
#include <stdio.h>
#include <stdarg.h>

void sum(int num_args, ...) {
    int val = 0;
    va_list ap;
    int i;

    va_start(ap, num_args);
    for (i= 0; i < num_args; i++) {
        val += va_arg(ap, int);
    }
    va_end(ap);
    return;
}
```

## Command-line arguments
Check `argc` and `argv`.

## Redirecting I/O

## Type Qualifier `volatile`
`volatile` suppresses optimisations.

## Suffixes for integer constants
| suffix | name |
|--------|------|
|`u, U` | unsigned int |
| `l, L` | long int |
| `lu`| long unsigned | 

## Suffixes for float constants
| suffix | name |
|--------|------|
|`f` | float |
| `ld` | long double|

## C preprocessor
The C preprocessor executes before a program is compiled.
Some actions are
- inclusion
- symbolic constants and macrors
- conditional compilation
- conditional execution of preprocessor directives.
They begin with `#` and only whitespace characters and comments may appear before a preprocessor directive on a line.
not expected to have semicolon.

### `include`
`<>` is for standard library definitions  
`""` is for locally-made definitions
The difference is where the preprocessor looks first.

### `define`
```c
#define [identifier] [replacement-text]
```
What's the difference compared to `const`?  
When the program starts, `[identifer]` will cease to exist, it is all replaced by `[replacement-text]`.

By convention, defines are named in `CAPITAL\_SNAKE\_CASE`

### macros
A macro is an identifier defined in a `#define` directive.
Macros may be defined with or without arguments.

```c
#define PI 3.14159265358979
#define CIRCLE_AREA(x) ((PI) * (x) * (x))
```
you may notice that we use `(x)`.
This is to enforce order of operations when something like `x = c + 2` is the input.

When macros are too long, we use `\` to indicate that the macro is in the newline.

### `undef`
```c
#undef PI
```
This gets rid of the `PI` definition.
As in the scope of the definition is between the `#define` and `#undef`.

### conditional compilation
```c
#if 0
// this will not be compiled
#endif
```

```c
#ifndef PI // or #if !defined(PI)
    #define PI 3.14
#endif
```

Other directives are also:
```c
#line 100 "some_file.c"
#ifdef
#elif
#endif
```

### `#` operator
This is for string concatenation
```c
#define HELLO(x) printf("Hello, " #x "\n");

HELLO("John");

#define y
```

## Predefined symbolic constants
File metadata.
```c
__LINE__ // number of lines
__FILE__ // filename
__DATE__ // date compiled
__TIME__ // line compiled
__STDC__ // 1 if compiled with standard C
```

## assertions
from `<assert.h>`
`abort` is from `<stdlib.h>`

# More About Final

