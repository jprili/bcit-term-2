Relational Database Systems
==
08 Jan 2025  
Alireza Davoodi  

> [!warning]
>
> This course has a group project!
> You can choose teammates (up to 3 others).
>

# Data
**Data**: Facts and statistics collected together for reference or analysis, typicall digitised.

Data is the new fuel for the global economy.  
Store it, find it and use it.

# Information and Systems
Q: What is information?  
A: Information is data put into meaningful and useful context and communicated to recipients who use it to make decisions

Q: What is a system?  
A: A system is a set of components that interact to accomplish some purpose. Examples are nervous, legal, banking, etc.

> [!note]
>
> Cheat sheet allowed in exams; A4/letter paper two sides.
> 

# Information Systems
Information systems are systems that manage information.
The key bulding blocks are Databases and Technology, and on top of that, inputs, processes, and outputs.

# Data Management
Data Management is an essential skill for future workforce.  
It can be used to:
* capture
* store
* retrieve
* analyse
* present
* interpret  
large amounts of data!

## Impacts
Data management is ubiquitous; it can be found all over commerce, government, and science and engineering.

# Database
A database is an organised collection of related data.
It represents some aspect of the real worlf, sometimes called the mini-world or the universe of discourse (UoD).
It is logically coherent with some inherent meaning, and it is designed, built, and populated with data for a specific purpose for an intaended group of users and some preconceived applications.

It can be of any size and complexity, and it can also be generated and maintained manually or it may be computerised.

# Database Management System (DBMS)
A DBMS is a software system for defining, ocnstructinf, and manipulating databases for various applications.

DBMS may be general purpose (business apps) or **special** purpose (biological DBs, geographic info).

> [!note]
> A DB is a file.
> A DBMS is a software.

## Components
1. Stored DB: A collection of related facts
2. DBMS
3. Applications
4. Users

## *The DB*
* Database Design (We will focus on this)
    Conceptual DB design
    Design Theory and Normalisation
* Data Models
    Relational, OO, Object-Relational, Network, Hierarchical
* Physical Storage
    Organisation
    Hashing
    Indexing

# Conceptual DB Design
Conceptual DB Design is very important phase in designing a successful DB application.

Step 1: Identify the UoD. The DB to be built will not model everything in the world, but rather some mini-world or UoD.

Step 2: Convert UoD to a data model.

# DB Design Theory and Normalisation
Redundancy Occurs when one fact is stored in more than one place.

**Example**

|ID|Name|Level|
|---|----|-----|
|1|Paris|Developer|
|2|Anna|Manager|
|3|Ben|Manager|

|ID|Name|Salary|
|--|----|-----|
|1|Paris|60,000|
|2|Anna|70,000|
|3|Ben|70,000|

Information about ID and name of employees is redundantly store in two different relations.  
Assuming an employee's salary directly corresponds...

# Relational Data Model
The relational represents the DB as a collection of relations.
This enables a conceptual model to be mapped into set of relations forming a DB.

# Complex relationships
A DB has the ability to represent complex relationships among the data.

# Applications
**Interface**: View Design, Interactive Querying, Host Languages, HCI
**Application Programs**: Functional Analysis, DFDs, Software Engineering

# Responsibilities of the DBMS
* Data Integrity Maintenance
* Query Processing
* Security Management
* Concurrency Control
* Backup & Recovery


