Combinations cont'd
==
14 Jan 2025
 
**Warm-up**:  
With students $A$ to $E$, how many ways can you select 3 students and put them in a sequence?
(Use permutation) How about a set? (Use combination)

> [!note]
> Assignment 1 (A01) out. Due 28 Jan.

Remember:
$$
n\text{C}r = \frac{n\text{P}r}{r!}
$$

**Example**:
A network consists of 10 servers with two subnets (NET1, NET2), each with 5 servers.
To crash a network, we need to crash exactly 7 servers.
How many ways can the attacker try to crash the network if:  
Q: The attacker must crash any 7 of 10?  
A: $10\text{C}7 = 120$  

Q: Exactly 3 from NET1, and 4 from NET2?  
A: $3\text{C}5 \times 4\text{C}5$a  

Q: The attacker must crash at least three servers from NET1?  
A: 
```math
2(5\text{C}3 + 5\text{C}4) + (5\text{C}5 \times 5\text{C}2)
```

**Example**:
Alice forgot her password for a mail account.
She remembers that the password was some arrangement of letters in CANADIAN, and had no adjacent As.
How many passwords does she possibly need to try?

Step 1: Arrange the not As.
\_\_\_\_\_  
Can be arranged in $5!/2! = 60$ ways.  

Step 2: Insert the As in between.
\^\_\^\_\^\_\^\_\^\_\^  
Can be inserted in $6\text{C}3$ ways.  
So in total, it would be $5!/2! \times 6\text{C}3 = 1200$ ways.

**Example** See counting combinations example with **RandInt** array.
```
counter = 15
for i = 1 to 6
    for j = i+1 to 10 
        counter = counter + 8;
    end
    counter = counter + 9
end
```
Q: What is the value of `counter` after the code finishes running?  
A: We can bruteforce the combinations of `i, j`. 
If `i goes to 9 (10 - 1)`, we have $10\text{C}2$ combinations.
Since `i` only goes up to 6, we still have 4 `i` values left.
Therefore
```math
10\text{C}2 - 4\text{C}2
```
and in total,
```math
\text{counter} = 15 + (10\text{c}2 - 4\text{C}2) \times 8 + 6\times9
```

If we have three nested loops, we would have $n\text{C}3$ and so on.

# Combinations With Repetition
**Example**:  
Suppose an alphabet has symbols A to D.
How many combinations of 3 symbols are there is you are allowed to repeat symbols in a combination?  
We can write down combinations with only one letter, two letters and so on. 
We should get 20 ways.

**Example**:  
How many ways can you distribute 12 toonie coins among three instructors, Carl, Goran, and Simin?  
We can represent each coin associated with each instructor as a string: 
e.g. `CCCCCCGSSSSS`  
We can use combinations with repetition.
With $n=3$ and $r=12$, we can represent each combination as:  
`xxxxxx|x|xxxxx`  
This is a mississippi problem.
How many ways can we arrange the dividers?  
A: 
```math
\frac{(12+2)!}{12!2!} = 14\text{C}2
```

> [!note]
> **Theorem**:  
> When we wish to select $r$ objects, possibley with repetition, from a set of $n$ distinct objects, the number of possible combinations
> (with repetition) is:  
> ```math
> \begin{pmatrix}
> n + r - 1 \\ 
> r
> \end{pmatrix}
> = \frac{(n + r - 1)!}{r!(n - 1)!}
> ```

In general, we can represent the above problem as a string of $r$ xs and $n-1$ barriers.
Then the number of arrangements is (from mississippi problem):  
```math
\frac{(n+r-1)!}{r!(n-1)!}
```
