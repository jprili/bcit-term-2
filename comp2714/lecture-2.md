Relational Data Model Constraints
==

# Functional Dependency
How can we know for sure if all employee members appointed appointed at the same level have the same salary?

Databases allow you to say that one attribute *determines* another
through a functional dependency.

Assume `level` determines `salary` but not `id`.
We say that there is a functional dependency from `level` to `salary`.
That is, if we know an employee's level, we can find their salary.

Functional dependencies introduces redundancy, so we must consider them in 
database and design.
If there is no functional dependency, there is no need for normalisation.

A functional dependency $X \rightarrow Y$ holds on relation $R$ if for every valid instance of $R$
such as $r$, for all tuples $t1, t2$:

```math
\text{if} ~ t1[X] = t2[X]; ~ \text{then} ~ t1[Y] = t2[Y]
```

It is a statement about all allowable instances,
and is identified by application semantics.

Given some instance of $R$, we can check if it violates some FD $f$ but we cannot tell if $f$ holds over $R$.
We can tell is $f$ holds over $R$ by using the UoD.

1. Come up with a miniworld
2. Come up with a model containing entities
3. Draw dependency diagram.

# Dependency Diagram
1. Specifying a Primary Key
2. Primary Key Dependencies: from PK to all attributes
3. Partial Dependencies: from a prime attribute to a non-prime attribute
4. Transitive dependencies

For each entity, come up with a model, and identifies all the dependencies.

# The Relational Data Model
Based on a sound theoretical foundation with a simple and uniform data structure called a *relation*.

## Relation 
The main construct for representing data in the Relational model.
Informally, a relation is a set of records, similar to a table with columns and rows.

## Components
A relation has a name, a couple of attribute names, tuples, and attribute values from the same domain.
A tuple is analogous to a row in a table.

## Domain Types
A domain $D$ is a set of atomic values.
An atomic value is indivisible (as far as the relational data model is concened).
Each domain has a data type of format (e.g. integer, number/currecy, Australian Telepone Numbers, Licence formats, etc.).

> [!note]
> Same attribute names does not necessarily imply the same domain,
> and conversely, different attribute names also does not imply different domains.

A tuple $t$ is an ordered list of n values:
```math
t = \langle v_{1}, v_{2}, \ldots v_{n} \rangle
```

## Schema
The schema is the information about the database.
Schema is data that describes the data of the relation.

A general format of a schema is

```
RelationName [primary_key, attr_name_1, attr_name_2, ..., attr_name_n]
```

## Ordering of Tuples
Mathematically, elements of a set have no implied order.  
Semantically, it is irrevelevant.  
Physically, ....  

# Integrity Constraints
Integrity constraints are specified on the DB schema.
They must hold on every instance of that schema, as well as on transitions of the schema.  

Integrity constraints enforced by DBMS include:
* Domain
    - A domain is a set of atomic values.
      Each attribute in a relation will belong to some domain.
      If we assign a string attribute to a domain that only accepts a 4-digit integer,
      the DBMS complains.
* Key
    - Uniqueness constraint: all $t$ in $R$ must be distinct.
      (i.e. no two tuples can have the same values for all attributes.)
    - A superkey (SK) is a subset of attributes of $R$, that forany two tuples
      $t_{i}$ and $t_{j}$ in a relation state $r$ of $R$
      ```math
      t_{i}[\text{SK}] \neq \t_{j}[\text{SK}]
      ```
      Every relation has at least one SK, and trivially is the set of all attributes.
    - $K$ is a key in $R$ iff (i) $K$ is a superkey of $R$, and (ii) $K$ does not contain any extraneous attributes.
      That is, any subset of $K$ is no longer a superkey of $R$.
      A key is a minimal superkey.
    - A key may have more than one key, each is called a candidate key.
      and one is selected as the primary key, which would be underlined.
    - A key must remain unique at all times.
* Entity integrity
    - The primary key cannot be null at any time.
    - For primary keys that consists of multiple attributes,
      no part of the primary key can be null.
* Referential integrity
    - Key and Entity integrity constraints are specifid on individual relations.
    - Referential Integrity constraints are specified between two relations and are based on the notion of
      foreign keys.
    - Foreign keys allow us to relation two different schemas.
      They can be viewed graphically or textually.
* Semantic integrity
    - Constraints that cannot be directly expressed in teh schemas of the data model referred to as semantic
      constraints or business rules.
    - Semantic constraints can be used to enforce organisation policies such as "salary of a manager is greater than employee".

## More on Foreign Keys
Let $\text{FK}$ be a set of attributes in $R_{1}$.  
Let $\text{PK}$ be a set of attributes in $R_{2}$.

$\text{FK}$ in $R_{1}$ is a foreign key referencing $\text{PK}$ in $R_{2}$ if:
* $\text{FK} and $\text{PK} have the same domain
* for any tuple $t_1$ in $R_1$, either $t_1[\text{FK}]$ is null; or there exists a tuple in $R_2$,
  such that $t_1[\text{FK}] = t_2[\text{PK}]$.

## Self-referencing Relations
It is also possible for a table to reference itself.
For example, a manager (also an employee) manages another employee.

## Relations with Composite Keys
It is also possible to have foreign keys to relations that have a multi-attribute primary key.

## Constraints and Operations
Enforcement of integrity constraints ensures that the database remains consistent.
Changes to the DB must not violate integrity constraints (leave the database in an inconsistent state).

## Transcation
A transaction is an executing program that includes some DB operations, such as reading, inserting, deletions, or updates.
At the end of the transaction, it must leave the database in a valid or consistent state that satisfies all
the constraints specified on the DB schema.

Transactions allow execution of a suite of queries where ...

# ER To Relational Mapping
Input: ER model  
Output: relations with primary/foreign key constraints.  

Steps:  
1. Entity Mapping
2. Weak Entity Mapping
3. Binary 1:1 Relationship Mapping
4. ...
