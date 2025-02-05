Aggregation, Inheritance, and Java Exceptions
==

# Fixed size collections
Useful wen the maximum collection size has been pre-determined.
Java arrays are a fixed-size sequential collection that can store object references or primitive type values.

## Declaration and Initialisation
```java
scope type[size] arrayName;
```

If the array is empty, it uses primitives to store initial values.
We can initialise using an array literal.
```java
scope type[size] arrayName = {contents};
```
This is the only time we can use an array literal;

Arrays do not have methods.
They only have a public property `arrayName.length`.

# Multidimensional Arrays
We can instantiate one with
```java
type[][] arrayName = new type[m][n];
```
The dimensions are not limited to two as well.

## Ragged Arrays
Arrays with non-rectangular shape.
We can instantiate one with:
```java
arrayName[i] = new type[j];
```

`System.arraycoppy()` copies an array faster than using a for-loop.

In `java.util.Arrays`, we can use `equals()`, `sort()`, `asList()`.

# The ArrayList
Under the "hood," the `ArrayList` is implemented with an array.
It requires a contiguous block of memory for the array.

When we instantiate an iterator object to loop through an
`ArrayList` using the `iterator()` method.

Remember: `ArrayList` is a class and the array is a collection (it's something else).
The `ArrayList` is 1D, but array can be multidimensional.

`ArrayList` is preferrable to array since it's OO, dynamic, and has many associated methods with it.
Array is used when the size of the collection is known and won't change.

# Aggregation
Aggregation is a special form of association.
It specifies a whole-part relationship between the aggregate (whole) and the component (part).
The whole can exist without the part.
Implementation of an aggregation is an instance variable.
Use a collection or array!

Composition and aggregation, is analogous to a mandatory and optional participation

# Inheritance
Inheritance is the relationship between a superclass and a subclass.
A subclass can only have one superclass.
We can add attributes, methods to the subclass,
as well as override superclass methods.

# `java.lang.Object`
This is the superclass of all classes.
Methods in Object are inherited by all classes.

1. `toString()`
2. `equals()`
3. `hashCode()`

# Overriding
Overriding is when a superclass and a subclass each ontain a method with the same signature.
The subclass version is specialised to a subclass.
The superclass satisfies static type check.

In the constructor of the superclass we use.

```java
public class SubClass extends SuperClass {
    ...
    public SubClass(...) {
        super(...); // pass the arguments up the tree
    }
}
```

The call to super must be the first line in the constructor.
Except in JDK 23, where we are allowed to validate parameters.
If the `super(...)` is not called, the compileer will insert a zero-parameter `super()`.

We must create the inner layer of the onion before we can wrap it with the outer layer of the onion.
Never break this rule.

# Superclass methods
We can call a superclass' methods with `super.methodName();`

# Multiple inheritance
Multiple inheritance is not allowed in Java.

# Designing for inheritance
* Inheritance makes the classes reusable and more flexibale.
* Common characteristics are upshed up the hierarchy.
* Every derivation must be from an is-a relationship.
* Overrie merhods as appropriate to tailor or change the dunctionality of a child.
* add new variables to children, but do not redefine/shadow inherited variables.
* Override general methods such as toString, equals, and hashCode.
* For methods that you don't want inherited, put the keyword `final` in the modifier.
* If don't want a class extended, add `final` to the class modifier.
* Private methods cannot be extended.

# Protected access
The `protected` visibility modifier makes a member visible and extendible in the super and subclasses, but not outside.

In a package, we can only find a hierarchy of classes. The parents, and the children.

Overriding can also loosen visibility modifiers.
When you override a method, you can make the visibility more public, but you cannot make it more private.

# Error situations
Trying to generate an inconsistent or an inappropriate object state.
Trying to make an illogical object request.
Dividing by zero.

## Exception
We bundle up our errors and exceptional situations into objects.
This is similar to a Python error.
Why do we bother with exceptions?

When a method encounters a problem it cannot handle, it must inform the method invoker of a problem.
Java exceptions formally separate error handling code from correct flow of control.

Every exception extends the `Exception` class.
It contains the
1. Exception type
2. location
3. stack trace

We throw exceptions.
We say that a block of code throws an exception out of its context into another context.

When an exception takes place, I can
1. Ignore it and let the program crash (do not do this).
2. Catch and handle it where it occurs
3. Throw it from the method where it occurred and catch and handle it at another place in teh program higher up the stack.

# Try-catch
```java
try {
    // Method that throws exception
} catch (final ExceptionType e | AnotherExceptionType f) {
    // Manage the exception
}
```
## Finally
No matter what happens, a finally clause is executed always.
```java
try {} catch {
} finally {
    // always executed
}
```

Catch subclasses first, otherwise the superclass exception will catch everything.
Order matters!

> ![note]
> Exceptions inherit from throwable.
> There are also Errors, which are thrown in compile time.

# Checked exceptions
A checked exception is an exception that extends exception directly.
The compiler checks that our code is handling it by forcing us to use try-catch.

# Unchecked exceptions
are subclasses of `RuntimeException`.
The compiler does not remind us of it.
It does not require explicit handling, though it could be processed that way.


