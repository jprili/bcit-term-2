Dependency Inversion
==

# SOLID recap

Interface and Inheritance for Open-Closed principle:
- Inheritance to extend the class
- Interface to create a "quasi-multi-inheritance"

Interface Segregation
- No fat/bloated interfaces

Program to an interface
- Interface as variable types
- Flexibility
- Create Methods that accept a list instead of arraylist.

# Dependency Inversion
Anything we include is a dependency and it must also be compiled.
Use interfaces as a middleman to a class.
A system is more flexible when source code dependencies are abstractions.

We want source code dependencies to point in the opposite direction to the flow of control.

- Abstractions Over Implementation
- Dependency Injections
- Inversion of Control

1. Don't refer to concrete classes, refer to abstract interfaces instead.
2. Don't derive from concrete classes.
3. Don't override concrete functions, make the funtions abstract and create multiple implementation.
4. Never mention the name of anything concrete.

Consider an application where a class directly depends on another (concrete class) for data access.
This direct dependency makes it difficult.
Instead, the class should depend on the interface.

# Abstract Factory
We can use abstract factory to manage undesirable dependencies.
Interface in-charge of creating an instance.
The instance is also implements from another interface.
This splits abstractions from implementations.

## Static Factory Method
Private constructor that does nothing,
but creates instances using method.

## Dependency injection
It's where we inject the required element as a parameter.
Dependency injection enables depedency inversion.

Benefits:  
- Decoupling
- Ease of Maintenacne
- Testability
- Scalability
- Code Quality

# Nested classes
- Static Nested Class
- Inner Class

These is a way to:
- logically group classes that are only used in one place
- a waus to increase encapsulation
- code can be easier to read and maintatain

Static nested class cannot be used to access the outer class members.

## Local classes (src/innerClasses)
Defined inside a block of code.
It has access to the enclosing method's parameters and local variables if thery are effectively final.
A variable is effectively finial if it is not modified after its initial assignment.

These are non-static since they have access to instance members of the enclosing block.
A local class can access a method's local variables if they are final or effectively final.

Remember closure.
The captures variables are effectively treated as finals.

## Anonymous classes
Something like this:

```java
 // some code inside a class

 ... new Worker() {
    { System.out.println("Inside instance initialiser") }

    public void doSomething() {
        // define it here.
    }
 }

```

Use cases:  
- Conciseness

Use a (page 13)  
inner class

# Lambda
Express instances of a single-method classes and interfaces more compactly.
Lessens the bulkiness of the code.
For some method, we can do this:

```java
printPersons(
    roster,
    (Person p) -> p.getGender() == Person.Sex.MALE
        && p.getAge() >= 18
        && p.getAge() <= 25
)
```
## Functional Interface
Any interface that only has one abstract method.

### Standard Functional Interfaces
- Predicate<T>: boolean 
- Consumer<T>: void
- Function<T, R>: R is return
