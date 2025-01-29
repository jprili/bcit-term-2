Abstraction and Relationships
==

We have multiple constructors with different information can instantiate a class.

`NumberFormat` and its methods have static factory method.

# OOP programmers love to reuse classes
When we create a class, we create a data type that other classes (and projects!) can use.
Classes use other classes as containers, components, colleagues, co-conspirators... etc.

1. How do classes relate to one another?
2. We know how to implement an individual class, but how should they interact?
3. How deeply should a class reach into another class, for example?
4. How do we implement associations between classes?

We want code that
* behaves correctly
* is soft (tolerates/is easy to change)

There is no such thing as a system that is impossible to change, but there are systems that practically
impossible to change, i.e., when cost exceeds benefit!

Software is not written once like a novel.
It is written, extended, etc.

# Responsibility-Driven Design
Each module of a system must have one responsibility.
Each module must perform that responsibility with minimal reliance on other modules.

Cohesion decreases when a class has more than one responsibility.
It increases between two classes between two classes A and B if:
1. A has an instance variable that refers to B
2. A uses B
3. A has a method that references B (via a return type or parameter)
4. A is a subclass of (or implements) class B

# Coupling and Cohesion
Coupling is the degree of interdependence between modules.
Cohesion is the degree to which elements inside a module belong together.
Less coupling and more cohesion maximises independence.

# Composition
Composition is how a class uses another class.
OOP envisions software as a collection of cooperating objects rather than ...

## unidirectional association
An object of one type contains an instance variable of another, aka, it manages a reference to an object
of another type.

## bidirectional association
Two objects contain references to one another.

A composition specifies a whole-part relationship.
A whole cannot exist without the parts.
The lifetime of the owned instance depends on the lifetime of the owner.
Be cautious about sharing references, remember scope and reference counting!

# Dependency
Dependencies exist when a class uses another as a parameter to an operation.
This is indicated by a dashed line pointing from the dependent (or client)
to the independent (or supplier) element.

# Delegation
We pass a reference to an object as a parameter to a constructor.
The wrapper-owner object guards the reference to its delegate.
When the wrapper-owner needs to perform a task, it pretends to know how,
but actually, but actually delegates the work directly to the instance variable.

# Law of Demeter
Supports loose coupling.
1. Each unit should only have limited knowledge about other units
2. Do not talk to strangers
3. Only talk to your immediate friends

# Standard IO
1. System.out is standard output
2. System.in is the standard input
3. System.err is defines standard error

err and out represent the console.
We can change the Streams with `setIn`, `setOut`, and `setErr`.

> ![note]
> When logging, use `System.err`

# Symbolic constants
We use `final` to define a symbolic constant. 
`ALL_CAPS` for class-level constances
and `lowerCamelCase` for local constants.

Reasons:
* Lends clear meaning to otherwise unclear literal values.
* Facilitates easier program maintenance
* Establishes formally that a value must not change.

If a variable will receive a value once and never change, make it final.
Every single parameter is final.
We can change the contents of an object, but we cannot change the address of the argument itself.
Setting the parameter to something else is redundant.

# Identity, equality, references, aliases
Equality refers to the state of the object, while identity refers to the address.
Remember we cannot store primitives in data structures.

# String Interning
If we have multiple `String`s that contain the exact same sequence of characters, the JVM may intern them for us.
Only a single copy is allocated memory.
Other `String`s point to the same copy.
The copy is stored in the **String Constant Pool**.
We can force this to happen by invoking the `intern()` method.
This is why we don't use `==` to compare `String`s.
Never assume that anything is interned.

In Python, interned integers are singletons, with only one instance.

# Equals Method
Equals is inherited from teh Object class (inheritance is next week)
Object defines three methods that we must *override* for every class we implement:
1. `toString`
2. `equals`
3. `hashCode`

The equals method always uses the same algorithm.

```java
@Override
public boolean equals(final Object object) {
    if (object == null) {return false;}
    if (this == object) {return true;}
    if (!(object.getClass() == this.getClass())) {
        return false;
    }
    
    ThisType other = (ThisType) object; // CASTING
    // compare fields and other stuff
}

```

When an object A receives a reference to another object B
of the same type, the first object A can directly access all of B's private instance variables.

```java
public class Student {
    private string name;

    @Override
    public boolean equals(final Object student) {
        // stuff
        Student otherStudent = (Student) student;
        return name.equals(...)
    }
}
```

# `hashCode()`
A hash function maps data of arbitrary size to data of a fixed size.
Takes a variably sized input and turns it into a fixed size output in a random-like manner.
A hash function generates ditinct integers for distinct object states.
Objects that are equal in state should return the same hash code.

# Hashing
Widely used in `HashMap`s.
The fastest access to an element is via an index, IF you know the index.
The IDE will automatically do it for you.

(algorithm in slides page 30)

## Collision
What if we store strings in an array?
Can we calculate a hash using unicode values for characters?
A String could be hashed as the total of the unicode values for the characters in the String.
This could result in collisions.

**Pigeonhole principles**:
If $n$ items are put into $m$ with $n > m$, then at least one container must contain multiple values.

## In Java
Java uses a `Map` instead of a dictionary.
Each key must be unique.
The map models the mathematical concept of a function. 
`HashMap` contains two things to help with collisions.
1. Initial capacity
2. Load factor

# Enumeration
Java allows you to define an enumerated type, 
a special kind of class, which can then be used as a type for variables in our program.
```java
enum Season {winter, spring, summer, fall};
```
An enumerated type declaration contains a list for all the possible values for a variable of that type.
The values are identifiers of your own choosing.
These are the only valies we can assign to a variable of that type.
Enumerations are implicitly final and have private constructors, so we cannot instantiate one.

We use enumerations when we need a set of constants whose members are known at compile time.
This includes "natural" enumerated types like planets, days of week, etc.

## `enum` and `switch`
We can use `enum` to provide conditions for `switch`.

# Class variables and Statics
A class variable is shared between all instances of a class.
In fact, it belongs to the class and exists independent of any instances.
It is designated by the `static` keyword.
Static variables are initialised once, at the start of exectution.

## Static variables
Public static variables are accessed via the class name;
e.g. `System.out` or `BouncingBall.gravity`.
Memory space is allocated when teh class is first referenced.

A static member is always present, no instantiation required.
It associated the method or variable with the class rather than with an object of that class.

What does this imply about the relationship between static members and non-static members?  
Static members do not have access to non-static members.

## Static initialisation block
Static initaisation block is a block of code and is surrounded by curly braces and preceeded by the `static` keyword.
It is executed once, and when the class is loaded for the first time.

# Comparing doubles
Just like Python, we cannot use the equality operator when comparing two floating points.
The `Double` class has its own `compare()` method.
