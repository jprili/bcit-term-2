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

> [!note]
> **Theorem**
>
> The number of permutations of $n$ disctinct objects is $n!$

**Definition**: An $r$-permutation is an arrangement of $r$ objects taken from a set of $n$ objects. 
The number of such $r$ -permutations is denoted $P(n,r)$ or $nPr$. 

**Example**: Consider the four objects $A$, $B$, $C$, $D$. The possible 2-permutations are: ... $4P3 = 12$ permutations.

**Example**: 3-permutations are from 26 letters? ... $26P2$.

> [!note] 
> **Theorem**
>
> $$
> \begin{equation} 
> \text{P}(n, r) = n\text{P}r = n (n -1) ... (n - r + 1) = \frac{n!}{(n-r)!}
> \end{equation}
> $$
> 
> $$
> \begin{equation}
> \text{P}(n, n) = n\text{P}n = n!
> \end{equation}
> $$

**Examples**: Consider passwords made up from the letters: "COMPUTER".
a. How many passwords have length 12?   
A: $8^{12}$

> [!tip]
> decimals in this course have 4 significant figures.

b. How many passwords have length 12 and all distinct letters?  
A: None! There will always be repetition.

c. How many passwords of length 8 have all distinct letters?
A: $8P8 = 8! = 40,320$

d.  Length 5 have all distinct letters?
A:  $8P5 = 8!/3! = 6720$

# Permutations with Repetition
**Example**: How many arrangement are there of the six letters in "CANADA"?  
Note that there are 3 As.

To account for repetition, we modify by labelling the As. Like $CA_{1}NA_{2}DA_{3}$.
There are $3!$ ways to re-order the $A$ s.

Therefore, the correct answer is $6! / 3! = 120$.

**Example** Find the number of arrangements of the letters in the word "MISSISSIPPI". 

A: We have 11 objects, with 1 M, 4 I, 4 S, and 2 P. We can then write the answer as
$11!/(4!4!2!) = 34650$.

> [!note]
> Theorem
>
> In general for $j$ indistinguishable objects, the number of arrangement is 
>
> $$
> \begin{equation}
> \frac{n!}{n_{1}!n_{2}!\ldots n_{j}!}
> \end{equation}
> $$

# Combinations
When we are counting ordered sequences of objects, it often helps to think in terms of permutations.

In other counting problems, the groups of objects are not ordered (or the order does not matter). 
For those problems, it helps to think in terms of combinations.

**Example**: How many ways can you put rings on two out of five fingers?  

A:  
$\text{C}(5, 2) = 5\text{C}2 = \begin{pmatrix} 5 \\ 2\end{pmatrix} = 10$

This is the same as asking "how many 5-bit strings have exactly two 1s" or 
"how many 5-bit strings have exactly three 0s".  
This is because choosing 2 leaves out three objects.

**Example** Consider 5 objects ($n = 5$).  
$P(5 , 3) = 5(4)(3) = 60$  
$C(5, 3) = \text{number of combinations} / \text{number of arrangements per state with the same objects} = 5(4)(3)/(3(2)(1))$

**Definition**: If $n$ distinct objects are available, a combination of $r$ objects (no order specified can be formed in $C(n,r)$ ways.

$$
C(n,r) = \frac{P(n,r)}{r!} = \frac{n!}{(n-r)!r!}
$$

**Example**: Suppose there are ten employees.
Q: How many ways can you select three employees to visit three different factories?
A: $P(10, 3)  = 720$. Microstate $E_{1}E_{2}E_{3}$ is not the same as $E_{2}E_{1}E_{3}$.

Q: How many ways can you select three employees to visit one factory together?
A: $C(10, 3) = 120$
