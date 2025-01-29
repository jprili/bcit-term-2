ER to Relational Mapping (Module 2 cont.)
==

# Steps for mapping
See p. 61 of module 2 slides

1. Entity
2. Weak Entity
3. 1:1
4. 1:N
5. M:N
6. Multivalued
7. N-ary
8. Super and subclasses

Steps 1 to 7 belong to the base ER, while step 8 is for extending the ER.

# Entity Mapping
Regular: non-weak entity with simple attributes.
Each entity type $E$, create an $R$ that includes all attributes of $E$.
* Include only simple component attributes of a composite attribute
* Don't include derived attributes
* Choose one key atribute of $E$ as primary key for $R$.

If we have an attribute $a_{2}$ composed of $a_3, a_4$
and a multi-valued attribute $a_5$,
`E[a1, a3, a4]`.

# Weak Entity
For each weak entity $W$ with owner $E$,
* Create an $R$ that includes all simple attributes of $W$.
* Include as foreign key attributes in $R$ the primary key attributes of $E$.
* The primary key of $R$ is the combination of the primary key of $E$ and partial key of $W$ (if any).

# 1:1
For each 1:1 type $r$, with participating relations $S$ and $T$,
* choose one relation (T) and include as foreign key T the primary key of S.
* It is better to choose the entity type with total participation in r.
* Include all the simple attributes (or the simple components of composite attributes of r as attributes of T)

see p. 74 of module 2 slides

# 1:N
Focus on the many sides.
Add the primary key on the 1 side as the foreign key on the many side.
The foreign key is not unique.
We don't need to create a new relation here.

# M:N
For each many-to-many relationship $r$, create a new relation $R$ to represent it.
* Include as foreign keys, the primary keys of the relations that represent the participating entity types in $R$.
* The combination of foreign keys will form the primary key of R.
* R can have its own attributes that contribute to the primary key
* Include any simple attributes of R as attributes of the new relation.

## Sparse Relationship Mapping
Note that 1:1 and 1:N can be mapped in the same way as M:N.
It reduces the number of `NULL`s.

# Multivalued attributes
For each multivalued attribute $A$, create a new relation $R$ that includes an attribute corresponding to $A$
plus the primary key $K$ (as a foreign key of $R$) of the relation that represents the entity type or relationship type
that has $A$ as an attribute.
* The primary key of $R$ is the combination of attributes $A$ and $K$
* If the multivalued attribute is composite, include its simple components

# N-ary
see page 93 of slides
We also create another table, rules for M:N and 1:N apply as well, in regards to the uniqueness of attributes.

# Super and subclasses
We have several options
## Multiple relations
We create a relational table for the superclass, and create a relational table for each subclass.
The primary key of each of the subclass is the primary key of the superclass.

Works for disjoint/overlapping and total/partial.

## Multiple relations for subclass only
We create a relational table for each subclass.
THe attributes of the superclass are merged into each of the subclasses.
The primary key of the subclass table is the primary key of the superclass.

Only works for disjoint total subclasses.
Does not work for
* Overlapping because of redundancy
* Partial because the relation may lose superclass entities not in any subclass

## Single relation with One type attribute
We create a single relational table for all subclasses and the superclass.
The attributes of the table is the untion of all attributes plus the attribute T
to indicate the subclass to which each tuple belongs.
T is `NULL` in tuples that do not belong to any subclass (for partial constraints).

## Single relation with multiple type attributes
We create a single relation for all subclasses and the superclass.
The attributes of the table is the union of all attributes plus $m$ extra boolean attributes for each subclass to
indicate whether or not the tuple belongs to this subclass.

It works for overlapping subclasses that are total/partial
It introduces a lot of nulls and not recommended if there are many attributes in subclasses.

# SQL
SQL is considered one of the major reasons for success of the relaitonal model in the database industry.
SQL provides an industry-wide standard for database access.
In practice, different products support different dialects of SQL.

It is a declarative language for users to specify what the result of the query should be, and the DBMS decides operations
and order of execution.

SQL is designed for data definition, manipulation, and control,
powerful enough to retrieve any piece of data from database.

```sql
select * from employee;
```
