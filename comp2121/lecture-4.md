Quantified Logic
==

Propositional logic have symbols like $p$ or $q$.
Quantified logic have predicates and quantifiers.

Take the statement "Justin Trudeau is the Prime Minister of Canada."
The object is "Justin Trudeau" and the predicate is "is the Prime Minister of Canada."

An object is anything we could give a name,
The set of all objects that we consider is called the *universe of discourse* (UoD).

Let the universe be: $U = \text{the set of all people in Canada}$  
Define the predicates:
```math
\text{PM}(x): x \text{is the prime minister of Canada.}
\text{M}(x, y): x \text{is the mother of } y
```

We can use quantifiers to make statements about various unnamed objects:
```math
\exists x \text{PM}(x)
```
Means there exists $x$ such that $\text{PM}(x)$.

```math
\neg \exists y \text{M}(J, y)
```
```math
\forall \exists y \text{M}(J, y)
```

# Open Statements
$x$ or $y$ is an unspecified variable, then $\text{M}(x,y)$ is neither true or false.
It is called an open statement.
The unspecified variables are called *free variables*.

# Quantifiers
## Existential quantifier
$\exists x p(x)$ means there is some $a \in U$ where the statement $p(a)$ is true.

To prove it, we need to find the $a$ which makes $p(a)$ true.
To disprove it, we need to show that $p(x)$ is false for $\any x \in U$.

## Universal quantifier
$\all x p(x)$ means for all $a \in U$ the statement $p(a)$ is true.
To prove it: test that $p(a)$ is true for all $a \in U$
To disprove it, give a counterexample.

# Bound variable
Once you apply $\exists x$ or $\all x$ to an open sentence $p(x)$, $x$ is no longer free; it beomes a *bound* variable. 
It is bound by the quantifier $\exists x$ or $\all x$.

# Negations of Quantified Statements
```math
\begin{align*}
\neg \all x q(x) &\Leftrightarrow &\exists x \neg q(x) \\
\neg \exists x q(x) &\Leftrightarrow &\all x \neq q(x) 
\end{align*}
```
