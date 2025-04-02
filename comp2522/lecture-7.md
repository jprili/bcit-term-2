Streaming 101
==

There's an easier way to iterate!
It goes something like this:
```java
iterable.stream().forEach(e->System.out.println(e));
```

## Stream
Sequence of elements that can be processed in a functional-style manner.

**CAVEAT**: If we are using `.stream()`, 
we cannot modify the elements in the streamed structure.

## Stream Pipeline
Consists of a source, zero or more intermediate operations, and a terminal operation.  
Source: Can be a collection, an array, or an I/O channel.  
Intermediate operations: transformations to the stream.  
Terminal Operations: Trigger the processing of stream and produce a result or side-effect.  

To reference methods in a pipeline, use a double colon.
```java
students.forEach(System.out::println);
```

## Filtering
The `filter()` operation produces a new stream containing elements that match a given predicate.
REMINDER: A predicate is a function/method that returns a boolean.
Also we use functional interface for reusability.

## `.collect`
Collect aggregates the input data into something.

## FlatMap
Flattens a stream of streams to a single stream.
If we have a `List<List<String>>`, this would be handy.

## Reduction
`reduce()` 

## Why use this?
- Conciseness
- Readability
- Lazy Evaluation
- Parallelism

Concurrency
==

## The rule of three
1. Code stuff up
2. Duplicate the code 
3. Refactor

## YAGNI
Don't implement something until it's necessary!

## DRY
Do not repeat yourself.

## Concurrency
Race conditions happen when transactions are incorrectly interleaved.

Benefits:  

- Do things at the same time
- Faster completion time

Disadvantages:  

- difficult debugging
- OS manages computations, no Java control.
- Each thread is non-deterministic
- additional overhead required

## Process
A program that is executing.
Think of a sandbox.

The OS is responsible for:  
- Creating and deletion of user and system processes
- Process synchronisation.

## Threads
Every process can own a thread.
A process can own multiple, acctually. 

They have their own program counter, register set, stack space, and state.

## CPU Time
A CPU's time is divided into slices.
These slices are allocated to processes and placed in a queue.
The processes may, in  turn, allocate slices to threads, also in queues.

## Context Switching
Multiple threads share one heap, but multiple processes don't.
