Control Structures
==

# Repetition Essentials
A loop is a group of instructions the computer executes repeatedly while some loop-continutation
condition remains true.
We have discussed two means of repetition:
1. Counter controlled (definite): we know in advance how many times the loop will be executed.
    - A control variable is used to count the number of repetitions.
    The control variable is incremented (usually by one) each time the group of instructions is performed.
    When the value of the control variable indicates that the correct number of repetitions has been performed,
    the loop terminates ...
    - It requires the name, initial value, increment/decrement, and a condition that tests for the final value.
2. Sentinel controlled (indefinite): it is not known in advance how many times the loop will be executed.

# for-loop
The possible syntax for for-loops are:
```c
for (exp1; exp2; exp3)
    statement;

for (exp1; exp2; exp3) {
    //statements
}

// compiler error without semicolons
// expressions are optional
for (;;) {
    //statements
}

// beware! logic error if not intended
for (exp1; exp2; exp3);
// This is useful in embedded systems
// to prevent race conditions.
```

> [!note]
> When defining a counter for a for-loop
> use `size_t` instead of `int`.

An interesting example:
```c
for (size_t i = 0, j = 0; ...; i++, j++);
```

Good practices:
1. Do not nest more than 3 times.
2. Indent properly.
3. ...

# do-while loop

Syntax:
```c
// one statement
do
    statement;
while (condition);

// multiple statements
do {
    statements
} while (condition);
```

# Logical Operators
Q: How many logical operators in C?  
A: three, `&&`, `||`, `!`.

Q: What would below print?
```c
int a = 0, b = 3;
printf("%d", a++ || b--);
```
A: `1`

# Switch Statement
A syntactic sugar for a complicated if-statement.
values for `case` need to be hardcoded.

# Break and continue
`break` in a loop will end it. No more execution.
Same goes for the `switch` statement.
It will only end the current level of the loop though.
So if you have a loop in a switch, using a `break` in a loop will end the loop execution but not the switch and v.v.

`continue` in a loop skips the remaining steps and go back to start of the loop.
In a while loop, don't forget to increment before continuing!

Q: What is something we can do to exit from a function?  
A: `return;`

