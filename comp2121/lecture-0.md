Counting: Permutations
==
# Discrete Math
In a computer, everything is *discrete*, meaning every object is built from a *finite* number of bits. There is no way to directly represent an irrational number or a continuous function.

**Example**: A physical sound is a continuous variation in air pressure, which we would represent mathematically as a real-valued function, $S(t)$. 

**Discrete math** is a set of topics dealing with countable objects (like) integers.
- Logical statements
- Sets
- Models of Computation
- Sequences and Recurrence Relation
- Graphs and Trees
- Optimisation

# Basic Counting Rules
We will begin discrete math with counting.
To solve a problem, you typically need to break down a complicated task into a series of simpler tasks.
Counting problems require algorithmic thinking.

## Examples
----
Q: How many different 8-bit binary strings are there?
A: $2^{8}$

Q: How many 8-bit binary strings start with 11 or start with 00?
A: $2^{6} + 2^{6} = 128$

Q: How many 8-bit string do NOT start with 11?
A: $3 * 2^{6}$ OR $2^{8} - 2^{6} = 192$

## Rules
### Rule of product
Suppose a task can be completed by doing task $A$ and then $B$, where $A$ and $B$ are independent of each other.

Assuming: $A$ can be completed in $m$ ways, and $B$ in $n$ ways.
Then: $A$ & $B$ can be completed in $mn$ ways.

### Rule of sum
Suppose a task can be completed by doing task $A$ or $B$, where it is impossible to perform $A$ and $B$ at the same time.

Assuming: $A$ can be completed in $m$ ways, and $B$ in $n$ ways.
Then: $A$ or $B$ can be completed in $m + n$ ways.

### Rule of Negation
Suppose a task can be completed by doing task $U$ in any way except for those ways that achieve task $A$.

Assuming: $U$ can be completed in $m$ ways, and $A$ in $n$ ways.
Then: not $A$ can be completed in $m - n$ ways.

**Example**: How many different binary tree structures are there that contain four nodes?

A: We can use brute force. That is, drawing all microstates of the tree with four nodes. In the end, we get $4  + 5(2) = 14$.

## Example
Consider the following program segment where `i` and `j` are `int`s.

Q: How many times is the print statement executed?
```
for i = 8 to 10 {
	for j = 3 to 6 {
		print(i - j)
	}
}
```

A: $3 * 4 = 2$. Think about the rule of product.

```
for i = 1 to n {
	for j = 3 to n {
		print i*j
	}
}

// assume n \gt 3
```
A: $n (n-3 + 1) = n^{2} - 2n$

```
for i = 1 to n {
	for j = i + 1 to n {
		print i*j
	}
}

```
A: $\sum_{1}^{n-1}x = \frac{(n-1)n}{2}$

# Permutations
**Definition**: Given a set of $n$ distinct objects, a *permutation* is any linear arrangement of these distinct objects. (By default, a permutation is without replacement)

**Example**: With three objects $A$, $B$, $C$, the possible permutations are:
$ABC$, $ACB$, $BAC$, $BCA$, $CAB$, $CBA$. Why 6 permutations? We have 3 options for position 1, 2 on position 2, and 1 on position 3, so the number of ways is $3 * 2 * 1 = 6$.

> [!note] Theorem
> The number of permutations of $n$ disctinct objects is $n!$

**Definition**: An $r$-permutation is an arrangement of $r$ objects taken from a set of $n$ objects. 
The number of such $r$ -permutations is denoted $P(n,r)$ or $nPr$. 

**Example**: Consider the four objects $A$, $B$, $C$, $D$. The possible 2-permutations are: ... $4P3 = 12$ permutations.

**Example**: 3-permutations are from 26 letters? ... $26P2$.

> [!note] Theorem
> $$
> \begin{equation} 
> P(n, r) = nPr = n (n -1) ... (n - r + 1) = \frac{n!}{(n-r)!}
> \end{equation}
> $$
> 
> $$
> \begin{equation}
> P(n, n) = nPn = n!
> \end{equation}
> $$