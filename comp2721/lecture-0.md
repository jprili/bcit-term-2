Computer Architecture: COMP 2721
==
Ayesha Anzer

We will be talking about hardware and software systems and how they interact with each other.

# Required Software
1. SMPCACHE
2. SimpleScalar

# Basic Concepts and Computer Evolution
What makes a computer more than just a collection of wires and chips?
How does it know what to do when you press a key or click a button?

In any system we have:
1. Input
2. Processing
3. Output

Imagine a house.
It has two main things, a blueprint and materials.
In computer, we have Architecture and Organisation as an analogue.
These two components make an entire computer system.

# Computer Organisation/Architecture
Computer architecture are attributes of a system visible to the programmer. It has a direct impact on the logical execution of a program.
Architectural attributes include:
* Instruction set
* Numbero of bits for data types
* I/O

Computer Organisation ...

# IBM System/370
Introduces in 1970, it included a number of models.
Coul upgrade to a more expensive, faster model without having to abandon original software.
Newer models are introduced with improved technology, but retain the same architecture so that ...

# Structure and function
Hierarchal system is a set of interrrelates subsystems.

Hierarchal nature of complex systems is essential to both their design and description.
Designers need only to  deal with a particular level of the system at a time.
They are concerned with the structure and function at each level.

Structure is the way in which components relate to each other.
Function is the operation of individual components as part of the structure.

> [!note]
> "component" can also mean "subsystem".

## Structure
The CPU has:
* Registers
* ALU: Arithmetic Logic Unit for computations
* Internal Bus: Thing that links the other components in the CPU
* Control Unit: Controls the instructions from the CPU
    * Control unit registers and decoders
    * Sequencing Logic
    * Control memory: Extra storage for micro-instructions

## Structural components
* CPU
* Main Memory
* I/O
* System Interconnection

## Function
there are four basic functions that a computer can perform
* Data processing: data may take a wide variety of formas and the range of processing reqs is broad.
* Data storage: short and long term
* Data movement: I/O, data communications
* Control: contuol unit manages the computer's resources and orchestrates the performance of its functional parts in response to instructions.

## Major elements of a multicore computer -- Core and cache
When a register receives an instruction from the CPU to find a word, the register searches the caches first.

* L1 cache is the first cache the register looks at (general purpose)
* L2 cache is backup
* L3 cache is shared memory between cores.

The higher level you go costs more performance.
If the register can't find the word in any registers, it calls the ram and the data is moved through the caches, from L3 to L1
and returns the word to the CPU.

In the core, there two kinds of cache: the instruction and data cache.
Each instruction and data cache can be L1 and L2.

BIOS: Basic I/O System

# IAS Computers
Vacuum Tubes were used for digital logic elements and memory.
IAs is attributed to John von Neumann.
Stands for Institute for Advanced Studies.
Basically a prototype for the subsequent general purpose computers.

# Registers
* Memory Buffer (MBR): This is where the word is located from memory.
* Memory address (MAR): 
* Instruction (IR): Contains 8-bit opcode 
* Instruction buffer (IBR): Temporary hold right hand instruction from memory
* Program Counter (PC): contains the address of the next instruction pair to be fetched from memory
* Accumulator and Multiplier quotient (MQ): Temporarily hold operands.

# Integrated Circuits
A computer consists of gates, memory cells and busses.
The gates and cells are constructed of simple digital electronic components.
Exploits the fact that such components as transistors, resistors, and conductors can be fabricated from a semiconductor.

# Transistors
The fundamental building block of digital circuits used to construct processors, memories, and other digital logic devices.
Has two states: conductive (1), and non-conductive (0).
It is a discrete component. 
They're manyfactured separately and packaged in their own containers.

A chip has an array of gates.
A wafer has an array of chips.
Chips can be packaged or in a wafer.

# Moore's Law
Number of transistors that could be put on a single chip was doubling every year.
Consequences:
* The cost of computer logic and memory has fallen.
* Electrical path length is shortened
* smaller computers
* recued power cost

MCM stands for Multichip Module

> [!warning] 
> Just think about numbers today compared to previouslly.
> (i.e. number of transistors, virtual memory)

# Embedded Systems
