Sequences and Series II
==

**Example** Given $a_{1} = 7$ and $a_k = 5 \times a_{k-1}$, what is $a^{100}$?
What is a general explicit formula for it?

A: $a^{100} = 5^{99}$, $a^{k} = 5^{k-1} \times a_{1}$  

**Example** Find a recursive definition for a sequence with a general term 
$a_{n} = 4n - 1, n \geq 1$.

A: We notice that it increases by 4 every iteration.
Therefore we have

```math
\begin{align}
a_{k} &= &a_{k-1} + 4 \\
a_{1} &= &3
\end{align}
```

# Summations
We use sigma to represent sums of sequences.
At the bottom, we have the initial equation, and the final value at the top.
To the side we have the general term/summand.
The variable in the summand is a dummy variable, name as you like.

We can also shift the starting point to rewrite the expression.
Make sure to change the starting, ending, and the summand accordingly.

**Example** Find the sum of $11^2 + 12^2 + \ldots + 100^{2}$.

A: 
```math
-\sum_{k=1}^{10} k^{2} + \sum_{k=1}^{100} k^2 = -\frac{10 \times 11 \times 21}{6} + \frac{100 \times 101 \times 201}{6} 
```

**Example** Find a formula for the sum of the first $n$ odd numbers.

A: Say $a_{k} = 2n - 1$.
We then have
```math
\sum_{k = 1}^{n} 2k - \sum_{k = 1}^{n} 1 = n^{2}
```

## properties
1. **Sum**:
```math
\sum^{n}_{k=m} [a_{k} + b_{k}] = \sum^{n}_{k=m} a_{k} + \sum^{n}_{k=m} b_{k}
```
2. **Coefficient**
```math
\sum^{n}_{k=m} c \cdot a_{k} = c\sum^{n}_{k=m} a_{k}
```
3. **Splitting**
```math
\sum^{n}_{k=m} \cdot a_{k} = \sum^{l}_{k=m} a_{k} + \sum^{n}_{k=l+1} a_{k}
```

# Code problems
```
counter = 100
for i = 0 to 10
    counter = counter + 2

for j = 1 to 20
    counter = counter + 3
    for k = 2 to 30
        counter = counter + 4
```

A: 
```math
\begin{align}
100 + \sum_{i=0}^{10} 2 + \sum_{j=1}^{20} \left[3 + \sum_{k=2}^{30} \right] &= \\
100 + 2(10 + 0 - 1) + 3\sum_{j=1}^{20} + \sum_{j=1}^{20} \sum_{k=2}^{30}4 &= \\
100 + 22 + 60 + 4 (29 \cdot 20) &= \\
2502
\end{align}
```

# Binomial Theorem
```math
(x + y)^n = \sum_{k = 0}^{n}
\begin{pmatrix}
n \\
k
\end{pmatrix}
x^{k}y^{n - k}
```

Since there would be $n\text{C}k$ combinations of either $x$ or $y$ from each bracket.
