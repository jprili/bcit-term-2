Introduction to Class and Foundational OOP Concepts
==

> [!note]
> Strongly typed: A Data type can only do things associated with the corresponding data type.

# `main`
We must add a method called `public static void main` to one of the classes to have an executable program.
This is where we instantiate the classes.
`main` must:  
- exist somewhere inside one of the classes in the program.
- be public so we could access it outside of the class itself.
- be static (class method)
- return `void`
- accept a `String` array parameter

`main` should create one or more objects, and ask one or more objects to do something.

> [!note]
> `static` is always available and in the heap.

# Elements of a class
```java
public class ClassName {
    // 1. Constants
    // 2. Instance variables
    // 3. Constructors
    // 4. Accessors and mutators
    // 5. Methods arranged locally
    // 6. Equals method
    // 7. Hashcode
    // 8. toString
}
```
## instance variables
We declare instance variables at the top of the class, unlike Python's `__init__`.
Its scope is the entire class -- all the constructors and all the methods can use it.

## constructor
Initialises a new object on by assigning values to all the instance variables.
The constructor must ensure that instance variables are set to initial values that are logical and valid.

The default constructor is:  
```java
public ClassName() {}
```

## accessors and mutators
Accessors are how we access the data in a class when the instance variable is private.
Mutators are used to chaned the data stored in an object's instance variables (state).
If a mutator rejects a value it does not do anything.
It fails silently.

## `this` 
`this` is used to the same instance of the object itself.
Used to overcome overshadowing (e.g. field vs. constructor argument).

## review
A Java object is an instance of a class.
It occupies a alocation in memory.
It encapsulates a state stored in its instance variables.
Each object is independent of each other.
The object is accessed through a reference which is a variable that stores the object's address.

# Encapsulation and Information Hiding
Java classes implement two fundamental OOP concepts.
1. Encapsulation
    * We put data inside the class with th emethods that manage it.
    * Each class is independent and responsible for exposing and managing its own state via public methods.
    * This means that state changes reliably and predictably.
2. Information Hiding
    * We wrap each object in an impenetrable barrier of privacy.
    * Distinguish between what is private (how an object performs its job) and public (how to interact with an object).

## Encapsulation
An encapsulated object can be thought of as a black box.
It is self governing -- it works independently, and its inner workings are hidden.
A client object invokes the public methods of the encapsulated object, which manage its own instance data.
Instance data and the methods that act upon it are together inside one impenetrable shell.

## Information Hiding
The implementation must remain private.
This decouples components:  
* Maintenance becomes easier because classes are less tightly connected 
* We can develop in parallel (after we agree on an interface)

## Difference
Encapsulation ensures that an object's internal state is protected from direct modification from the outside.
Information hiding minimises the interdependecies between parts of a program, making it easier to understand, maintain, and modify.

# Interface vs Implementation
A class' public interface is composed of its public constructor(s), methods, and constants.
We can call the class' public interface its API.
We say that "only the API is visible", we "expose the interface".
It's nobody's business how they do their job.

> [!note]
> Primitive lives where it's declared.
> So primitive instance variables in the class are also stored in the heap.

# minimise moving parts
Mutability should be minimised.
It is correct in Java for a mutator to react by doing nothing,
(i.e. if a potential value is null or too low or too high etc., then do nothing)

Minimise the side effects as well.
Accessors must not have any side effects, and mutators should only change the implicit argument.

1. Minimise scope of local variable, and make all instance variables private.
2. Make as many instance variables immutable to reduce moving parts.
3. Do not provide a mutator for an instance variable unless necessary. 
4. Do not provide accessors for mutable objects, if we do, the objects can be modified without permission.

# Responsibility-Driven Design
Okay so we hide informaiton by minimising scope, mutability, and visibility.
Classes employ self-governance. each class must be responsible for manipulating its own data.
RDD leads to high coherence (self-contained) and low coupling (least dependency).
One aim of reducing coupling and using responsibility-driven design is to localise change.
When a change is needed, as few class as possible should be affected.

Each module of a system must have only one responsibility.
Each module must perform that responsibility with minimal reliance on other modules.
This supports encapsulation.
we call relying on other classes coupling; keep this minimised.

Coupling increases between two classes `A` and `B` if:  
1. A has an instance variable that refers to (is of type) B.
2. A uses object B as a local variable inside a method or block of code.
3. A has a method that reference B (via return type or parameter).
4. A is a subclass of (or implements) class B.

# SOLID
Write code that is understandable, flexible, maintainable, and pleasant to work.
* **S**: single responsibility principle
* **O**: open-closed principle
* ...

# Unified Modelling Language (UML)
Key Components:  
1. Class name
2. Attributes
3. Methods

# Methods
The name of the parameter in teh method declaration is called a formal parameter.
Local variables are not automatically initialised to default values.
They must be explicity initialised to a value in an assignment statement before they are used. 
You can in classes, but not inside the classes' methods.

# Helpers
We minimise the number of public methods.
We only expose what *must* be exposed.
Helper/auxiliary methods *must* be private.
It is often the case that a class has a few public methods and many private helper methods.
Users don't need to know anything about HOW we provide our service.
When we invoke a method from inside the same object, we can optionally use `this.methodName(parameters)`.

# Overloading
Overloading occurs when there are several different signatures for a method with the same name.
Overloading constructors is allowed.
This removes duplicated code.
Solution: pass the arguments from the partial constructors to the main one.
