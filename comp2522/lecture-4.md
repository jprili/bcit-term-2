
# More On Exceptions


> ![note]
> Call to `super` is always first in a constructor  
> EXCEPT for validation and error throws.
>
> If you have a subclass, Java will do it for you in compile time.
> `super` is called without an argument to construct the parent class.

In Python we have EAFP, in Java it's LBYL.
This is so that we can check the if the parameters are valid before throwing.

# Kinds of exceptions
All exceptions inherit from `Throwable`.

Exceptions are Checked or Unchecked in Java.
Checked exceptions are found in compile time, while unchecked ones are found in runtime.

# Throwing checked exceptions
Methods that throw a checked exception, has a Javadoc and it is included in the header.

# Throwing vs. try-catch
Java methods which specify which checked exceptions they throw, or they can use try-catch and deal with exceptions internally.

A method must handle an exception right there by wrapping the code in a try-catch, or it must throw it.

# Inheritance Mixing with Exception
The superclass must handle more exceptions than the subclass.

# Lost exception
If an exception is thrown and then a second exception is thrown in a finally block, the first exception is lost.
Every instructor shows students this!
Don't do it, it's sloppy coding.

# Custom exception
Just extend from Exception with a new class.

# Controversy
Java does not require handling of unchecked exceptions.
But it is bad practice.

> ![tip]
> If we do not expect a client to recover from an exception, use an
> Unchecked exception.

Open-closed principle
==
Software artifacts should be open for extension but closed for modification.

A module must accomodate new functionality as requirements evolve (open for extension).  
The source code of a module should not be changed once it is written and tested (closed for modification).  

# Reasons
We use OCP to improve:
1. Maintainability
2. Scalability
3. Flexibility

A module is open if it is possible to modify the source code.
A module must be closed before it is available for use by other modules.
A closed module may be published in a library for others to use.

Never modify source code in classes that are already in use.

# Polymorphism
The condition of occuring in several different forms.
A feature of a programming language that allows routines to use variables fo different types at different types.

## casting
Using an object type in parentheses to th eleft of an assignment statement.
It is used to overcome type loss.
The object is not changed in anyway.
Can throw a ClassCastException (?).

Polymorphism is an IS-A relationship.
It has nothing to do with primitives, it's all about classes and objects.
Java lets us assign the address of a subtype object to a supertype variable.

# Polymorphism II
1. Static type (compile time)
2. Dynamic type (runtime)
3. Method dispatch/lookup

Every object has two types, static and dynamic type.
The static type is the type declared, while the dynamic type is the actual object the vairable points to.

During execution, Java executs the version of the method in dynamic type of the variable, if the dynamic type overrides the method.

Java uses the dynamic type in the method lookup, so if we have something like
```java
Animal animal = new Dog();
animal.move();
```
Java will use `Dog`'s '`animal.move` method.

Polymorphice method dispatch is choosing the method to execute during runtime.
Resolution (choosing the version we use can be early/compile or late/runtime).

# Method lookup algorithm
1. A variable and its data type are accessed (static type).
2. The object whose address is bound to th evariable is retrieved.
3. ...

We use polymorphism because
1. reduces duplicate code
2. makes code reusable
3. adheres to open-closed principle

# Polymorphism vs Duck Typing
Java does not use duck typing. 
It uses polymorphism with static and dynamic types.o

# Order of initialisation
1. Subclass calls its superclass constructor until it reaches `Object`.
2. Then instantiate the object.
3. Then do the rest in the subclasses.

# Warning: Constructors and overriden methods
In Java, during a subclass object's initialisation, if the supercalss constructor invokes a method that has been overriden by the subclass, the superclass constructor will use the subclass' version of the method.
Constructors should only invoke final methods.
Final methods cannot be overriden.

# Abstract class
`abstract class` is a class that is declared abstract.
An abstract method is a method that is declared abstract and lacks an implementation (no curly braces.)

They cannot be instantiated.
They could be thought of "incomplete superclasses"
They support polymorphism, and provide a foundation for a class hierarchy.

ALso, absract classes may have static fields and static methods.
They may also have instance variables that are not static or final.

By default, abstract is public.
Classes inheriting from an abstract class must implement the superclass' methods, otherwise the subclass must be abstract as well.
