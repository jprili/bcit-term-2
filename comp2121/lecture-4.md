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
