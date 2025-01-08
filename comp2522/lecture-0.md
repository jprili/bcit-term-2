Introduction to OOP and Java
== 

# Outline
1. OOP
	1. Encapsulation
	2. Inheritance and Polymorphism
	3. Decomposition and Abstraction
	4. Dependency Inversion
2. Inner classes and Lambda
3. Generics
4. Data structures (graphs, trees, linked lists)
5. Concurrency
6. Time and Space Complexity

# History
James Gosling at 1995. Simple, object-oriented, distributed, robust.

Java's great for mission-critical, server-side backend infrastructure.
Also architecture-neutral.

# How Does It Work
All source code is written in `.java` files.  
`.java` files are **compiled** to `.class` that contain Java Bytecode.
We execute the `.class`.
Java bytecode is executed "just-in-time" (JIT) in an instance of the Java Virtual Machine (JVM), and the JVM **interprets** the bytecode.

# Class
The fundamental programming unit is the **class**.
Objects are created/instantiated in the heap using a class as a template.
The code in a `.java` file describes a single class:
* What sort of data it contains
* How to instantiate it
* How do we interact with it

# Java
Java is Object-Oriented.
Every Java program creates a collection of objects that work together. 
...

1. All java statements end with a semicolon
2. Indentation is critical for developers, and semicolons are critical for the compiler.
3. Curly braces mark the beginning and end of block.

Java is case sensitive, and its identifier can be made up of letters, digits, the underscore character, and the dollar sign.

> [!note]
> constants in methods are `lowerCamelCase`
> outside of methods is `UPPER_SNAKE_CASE`

# types
Remember that python is strongly typed and dynamically typed.
Java is also strongly typed, but it is statically typed.

# Declaring and Initialising Variables
A variable is composed of a data type and an identifier.

In methods, when you declare a variable, you have to assign a value to it immediately.

# Primitives
Primitives are special in Java.
There is no special object created in the heap. 
The value is stored in on the stack inside the method where it is used.

Primitives can only store data within a specified range.
Their size and nature is the same in all platforms.

`int` (32 bits), `double` (64 bits), `boolean` (1 bit) are widely used today.
When a type over/underflows, it loops around the range (e.g. for `byte`, if you increment `127`, you'll get `-128`).

# Conversions
There are two types of conversions:
* Widening: the target data type has a bigger size, they are automatic, though may lose precision (from long to float). 
* Narrowing: the target data type has a smaller size. They are not automatic, and may lose magnitude and precision.

1. Assignment conversion 
```java
byte smallValue = 127;
int widerType = smallValue;
```

2. Promotion: widening that occurs automatically in arithmetic expressions that combine types (just like in Python).

3. Casting: most powerful and dangerous technique for conversion. Both widening and narrowing conversions can be accomplished by explicitly casting a value.

```java
int total = 50;
double result = (double) total / 6;
// without the case, the fractional part would be lost
```

# Control structures
Just like python, we have
## selection
1. If-(else if)-else
2. conditional operator
3. switch

## repetition
1. while
2. do-while: guaranteed to run at least once.
3. for loop (indefinite)
4. for each (definite)

## String
The Java `String` is an immutable sequence of primitive char (unicode code points) surrounded by codepoints.

We cannot compare the values with `==`. We do it with `.equals()`.
```java
String drink = "champagne";
String anotherDrink = "hard liquor";
boolean same = drink.equals(anotherDrink); // false
```

Strings are concatenated with the `+` operator. The language will try to concatenate 

# Objects
If a variable is not primitive, then the variable is an object roference.
So:
* A variable whose data type is a primitive stores a value.
* A variable whose data type is a class stores an address

# null
A null indicates an unset reference. We cannot assign `null` to primitives.
```
String name = null; // correct
int number = null; // wrong
```

# new
We use `new` to create an object by invoking a constructor.
The syntax is 
```
ClassName variableName = new ClassName(parameters);
```

# The JVM
The JVM permits cross-platform distribution of executable `.class` files.
It manages and optimised memory.

Bytecode that is executed frequently is optimised and compiled directly into machine code.

# Memory model
Java's memory model is like Python's!
1. Stack of method calls (main is on the bottom).
2. Heap of allocated objects.

# String interning 
Java may intern strings for us. No one really does it but if we want we can use `intern()`

# Data Structures
| python | java |
|--------|------|
| `list`   | `ArrayList<E>` |
| `dict`  | `HashMap<K, V>` |
| `set`    | `HashSet<E>` |

> [!note]
> We cannot store primitives inside collections!
> We must use wrapper classes!

## Wrapper classes
Wrapper classes encapsulate primitives.

**autoboxing-unboxing**: automatic class conversion to wrappers.

```java
private ArrayList<Integer> markList;
public void storeMark(int mark) {
	markList.add(mark); // Autoboxing
}
int firstMark = markList.remove(0); // Unboxing
```

# Scanner
The equivalent for Python's `input()` is through the `Scanner` object.
1. `import java.util.Scanner`
2. instantiate and identify the data source i.e. `System.in` or a file
3. use `next()`, `nextInt()`, `nextLine()`, ... to parse a piece of input of a specific type from that source.

> [!note] Issues with `Scanner`
> When calling `next` methods make sure to clear the buffer so there's no newlines lef. 
