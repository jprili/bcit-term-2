ARM Assembly I
==

# CISC vs RISC
Complex vs Reduced. x86 vs ARM
CISC is written in microcode.  

Microcode - Each processor consists of a subcomponent, 
            each subcomponent is written in microcode.
            
CISC could lead to loss of performance,
and better to use combinations of simple instructions. 

RISC has single cycle per instruction.
Less circuitry, and has simpler design.

# ARM
Advanced RISC Machines.
32-bit RISC processor architecture family.
It has many variants.
ARM itself does not make chips, 
but it licences the IP core logic design to chip manufacturers.

## Memory
ARM has linear addressing.
Linear addressing:
    We are saying that in a stack of memory,
    addresses in order.

It has two descending stacks:
* main
* process -- used by OS

Descending meaning that memory is allocated from top to bottom.
All operations are based on registers,
must move data between registers & memory.

Whenever we are trying to store and retrieve operation,
we are only using registers in assembly.

## Registers
16 * 32 bit registers.  
* R0-R12 are the working registers
    - 0-7 is low
    - 8-12 is high
* R13 is the stack pointer
* R14 link register: we are looking at all the function associations with each function that we have
* R15 program counter: tracking where the code is in the count
* PSR program status register:
    - CPSR (Current) and SPSR (Saved)
    - bits for negative (N), zero (Z), carry (C), and overflow (V)

## Data
Word is 32 bits, `long`
half word is 16, `int`
byte is 8, `char`

# Programming approach
- in high level, identify variables and types
- compiler maps these to memory and data representation
- use of memory v registers

- In low-level, must make explicit use of memory and registers
- must choose data representation

what if more variables than registers? (question in final)
- Spilling: move contents to main memory temporarily
- Prioritisation: it will look at the number of words we are trying to access.
                  store least frequently used (LFU) words in main memory
                  the most frequently used (MFU) stays in registers.

# Instruction format
```
instruction Rd, Rn, operand
```
instruction is mnemonic.

## `mov`
This is the assignment operator.
```
mov rax, 1
```
`movs` is the same as `mov` but update the condition flags

## label
identifier can precede any line of assembler.
may start with `_`.
Turned into program count + offset in machine code.

## system calls
`SWI 0` is the software interrupt to call function
`EXIT 1`.

## comment
`@` is a way to denote the comment

## addition and subtraction
`ADD`, `SUB`, `MUL`

## CMP
Subtract operand 2 from operand 1 but do not modify O2.
Flags are updated.
Flags: 
* N = 1 if result less than 0;
* Z if  result  = 0;
* C = 1 if result let to carry; 0 otherwise

# B
for branching.
B means branch to label.
B cond label

## Conditions
* EQ; Z = 1
* NE; Z = 0
* CS/HS; C = 1
* CC/LO; C = 0
* MI: N = 1
* PL: N = 0
* VS: V = 1
* VC: V = 0

# Assembly

```s
@ ARMv7 generic
.global _start @ analogous to #include <stdio.h>

_start:
    @ ARMv7 is case-sensitive
    MOV r0, #3 @ assign 3 to r0
    MOV r1, #5 @ assign 5 to r1

    ADD r2, r0, r1 @ r2 = r0 + r1
    SUB r3, r1, r0 @ r3 = r2 - r0    
    MUL r4, r3, r1 @ r4 = r3 * r1

    SWI 0
```

# directives
we can "define" data with `.equ X, 3`


