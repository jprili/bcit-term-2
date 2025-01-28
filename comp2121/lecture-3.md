Propositional Logic
==

# Definition
A proposition/statement is a sentence that is either true or false.
We denote individual propositions using the letters $p$, $q$, $r$, and so on.

Propositional logic deals with how simple propositions are combined into compound 
propositions using logical connectives.
(look up a $\LaTeX$ symbols on logic.)

**Example**:
"Either Lizzy is sleeping on the couch, or carl is not the Prime Minister of Canada;
and if Carl is the PM of Canada, then Tara is eating ice cream."  
A: $(q \lor (\neg p)) \land (p \implies r)$

Assuming $p$, $q$, and $r$ are false, is the compound statement True or False?  
A: $(F_0 \lor F_0) \land (F_0 \implies F_0)$ is True.

> ![note]
> $0 = False = F_0$  
> $1 = True = T_0$

Review your truth tables!

# Implies ($\implies$)
If $p$ then $q$.

| $p$ | $q$ | $p \implies q$ |
|-----|-----|----------------|
|0    |0    |1 |
|0    |1    |1 |
|1    |0    |0 |
|1    |1    |1 |

The first two cases are called "vacuously" true.

# Biconditionals ($\iff$)

| $p$ | $q$ | $p \iff q$ |
|-----|-----|----------------|
|0    |0    |1 |
|0    |1    |0 |
|1    |0    |0 |
|1    |1    |1 |

If both inputs are the same, $p \iff q$ is true.
Analogous to an equal sign.

# Tautology and Contradiction
A tautology or tautological statement is a compound statement that is true for all truth values of its propositional variables.
We uuse $T_0$ to represent a tautological statement.

A contradiction is a compound statement that is false for all truth values of its propositional variables.
We use $F_0$ to represent a contradictory statement.

**Example** Prove that $p \lor (\neg p)$ is a tautology and $p \land (\neg p)$ is a contradiction.  
A: Draw a truth table for each. They should show all $1$s for $p \lor (\neg p)$ and all $0$s for the latter.

# Logical Equivalence
Two compound $s$ and $t$ are logically equivalent if $s \iff t$ is a tautology.
We then write $s \iff t$. 

> ![note]
> CORRECTION:
> Biconditionals ($\leftrightarrow$) can be true or false, but logical equivalence means the biconditional ($\iff$) is always true.

No-name identity: $p \implies q \iff (\neg p) \lor q$

# Rules of Inference
In mathematics, an argument is a sequence of statements (called premeises) that ends with a conclusion.
An argument is valid if the premises logically imply the conclusion.
In other words, if the premises are all true, then the conclusion must be true.

## valid arguments
**Modus Ponens**
If $p$ then $q$  
$p$  
$\therefore q$  

**Modus Tollens**
If $p$ then $q$  
$\neg p$  
$\therefore \neg q$  

In general, an argument can have $n$ premises $p_1, \ldots, p_n$.
The argument
```math
p_1 \\
\vdots \\
p_n \\
\therefore q
```
is valid as long as $(p_1 \land \ldots \land p_n) \implies q$ is a tautology.

# Proof by Contradiction
Assume the conclusion is false, then combine with the other premises to derive a contradiction, $F_0$.
