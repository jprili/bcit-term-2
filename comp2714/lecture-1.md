Conceptual Data Modelling: The Entity-Relationship Model
==
Introduction to Information Systems  
15 Jan 2025

> This is a subjective module.
> - Alireza

# Conceptual DB Design
A very important phase in designing a successful database application.
Steps to design a database:
1. Identify the Universe of Discourse (UoD).
2. Convert the UoD to a data model, which can be caputred by a database.

A model is never perfect, though.
There are phenomena that are not captured in the model,
like some employees go out for dinner on Fridays.
Common phenomena is captured, but there are things true in the model, 
and not necessarily true in the real world.

# Entities and Relationships
Entities are the basic concept that the ER model represents, 
which is an object with a physical or conceptual existence.
An entity has attributes, which are the particular properties that describe it.

When you assign an attribute to an entity, that entity type becomes a specific entity.
Each entity tupe is described by its name and attributes.

In an ER, the entity type is represented by a rectangular box, 
and the attribute names are represented by ovals attached to their entity type.
Keys are applied to entity types, they are unique,
though there can be multiple keys (at least 1) for an entity type.
In the ER, they are are underlined.
The key *must* hold for every possible extension of the entity type.

We must use what is given to us in the mini-world.

## Composite vs. Simple Attributes
Composite attributes can be divided into smaller parts which represent simple attributes with different meaning.

Also, we can have composite keys.
Sometimes, several attributes together form a key,
meaning that the combination of the attribute values must be distinct for each entity.
If a set of attributes possesses this property, the proper way to represent this in the ER is to define a composite attributes.

## Single vs. Multi-valued Attributes
Simple attributes can either be single or multi-valued.
Multivalued attributes are shown with double-lined ovals and can have multiple values (e.g. one person can hold multiple degrees).

## Stored vs. Derived Attributes
Derived attributes can be obtained from stored attributes.
For example, the `Age` (derived) can be calculated from the `BirthDate` (stored).

## Value sets of Attributes
Value sets specify the set of values that may be assigned to a particular attribute of an entity.
Example: `employeeAge` is between 21 and 65.
In the ER, this is not displayed.

`null` is used if an attribute may not have an applicable value (missing, not known, or not applicable).

## Entity Set
The collection of all entities of a particular entity type in the database at any point in time is referred to as an entity set.
An entity set can be mapped to a table.

# Relationship Types
A relationship is an association among two or more entities.
A relationship type defines the relationship (represented with a diamond).
In this ER, no Entity-Entity connections!
It may have descriptive and key attributes as well,
but it does not need to.

## Relationship Degree
The degree of a relationship type is the number of participating entity types.
2: Binary  
3: Ternary  
n: n-ary relationship  

## Entity Roles
Each entity type that participates in a relationship type plays a particular role in the relationship type.
The role name signifies the role that a participating entity from the entity type ...

## Recursive Relationships
Same entity types can participate more than once in the same relationship type under different "roles".

## Relationship Set
This collection of all relationships of a particular relationship type in the database at any point in time is referred to
as a relationship set.
There are different methods of representing relationship sets.

# Relationship Constraints
Constraints limit when a participation is mandatory or not.
Cardinality: how many can participate.

## Cardinality Ratio
A cardinality ratio for a relationship set specifies the number of relationships in the set that an entity can participate in.
We have:
1. 1:1
2. 1:N (and v.v.)
3. M:N 

# Existence Dependency
Single line is partial (not required to participate)
and double line for total (required) participation.

# Weak Entities
Entity types that do not have key attributes of their own are called weak entities.
A weak entity can be identified uniquely only by considering a key of another owner entity
and its own partial key, which is underlined with a dotted line.

The relationship that relates a weak entity to its owner(s) is called the
identifying relationship.
A weak entity and its identifying relationship are represented with double lines.
Weak entities are always mandatory.
Example: An employee insures a dependent.
If the employee leaves, the information for dependent is no longer needed.

# The EER Diagram
The Enhanced/Extended ER Model is an ER model with concepts such as superclasses and subclasses.

## Specialisation
Deine a number of subclasses of an entity type.
Each subclass contains a subset of entities from the superclass. 
A subclass is defined based on more specific distinguishing characteristic on entities of the superclass.

## Generalisation
Abstraction is the process of ignoring differences amongst some subclasses and generalise them into a superclass.

# Constraints
Specialisation may be total (double line) or partial (single line). 
And the subclass sets may be overlapping (o circle) or disjoint (d circle).
