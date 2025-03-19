Generics
==

# Generating an iterator
We can use `.iterator()` on a collection to return an iterator.
1. `hasNext()`
2. `next()`
3. `remove()`

# Interface Segregation
An interface must be atomic.
It must have the smallest amount of "Implementables" in the interface.
If our class must implement unecessary methods in the interface, the interface may be too big.

# Linked List
Self-referential collection.
Head is the start.
The end points to `null`.

# Time and Space Complexity
1. Time efficiency: how much time does an operation take.

```math
T(n) = \text{num. of operations as a function of input size } N
```

# Big O notation
Let $f(n)$ and $g(n)$ be funcitons that maps the set of positive integers $\ZZ$
to the map of positive real numbers $\RR$.
We say that $f(n) \in O(g(n))$ if there exists some pos.
constant real number $c$, and some number $n_0$.

Suppose the amount of work we do increases linearly when a collection grows.
This is $T(n) \in O(n)$.

Extra: linearithmic is $O(n \log n)$
