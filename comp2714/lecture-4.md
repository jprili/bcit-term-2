SQL
==

# Syntax
```sql
CREATE TABLE "table name"
```

We also have to add the scema when we are creating the table.
For example:
```sql
CREATE TABLE Movie
    (movieID INTEGER,
     title   CHAR(20),
     year    INTEGER,
     PRIMARY KEY (movieID))
```

Don't forget the foreign keys with the `FOREIGN KEY` and `REFERENCES` keywords.
Also, if we want attributes to be non-nullable,
we add the `NOT NULL` keyword.

## constraints
To add constraints, we can use `CONSTRAINT <name> <constraint>`.
Semantic constraints are added with the `CHECK` keyword.
These constraints are checked when a tuple is added or modified.

# Forcing referential integrity
What should be done if an employee tuple is deleted, and there is another tuple that refer to it?
1. Delet all roles that refer to it?
2. Disallow the deletion of the employee?
3. Set mgrSSN in the employee tuples that refer to it to null?
4. Set mgrSSN to a default value?

We can use 
```sql
ON DELETE SET NULL | SET DEFAULT | CASCADE
ON UPDATE SET NULL | SET DEFAULT | CASCADE
```
`CASCADE` is analogous to rerouting from one data value to another.
`DEFAULT` is set in the table definition, something like
```sql
CREATE TABLE table_name(
    attribute DATA_TYPE DEFAULT(default_value)
)
```

# alter table
`ALTER TABLE` is used for *schema evolultion*.
We use this when we are adding or dropping columns,
changing column definition, or add constraints.

Examples:  
Adding an attribute
```sql
ALTER TABLE Employee ADD job VARCHAR(12);
```

Dropping an attribute
```sql
ALTER TABLE Employee DROP address;
```
To drop an attribute which has been used by other tables in their FK references, `CASCADE` can be used.
This means that if the PK is a FK somewhere, the deletion propagates to the FK tuple.

# dropping a table
Use `DROP TABLE`

# Manipulation (DML)
Data Manipulation Language is the other main part of SQL.

## `INSERT`
This is used to ad dtuples to an existing relation.  
Single tuple `INSERT`:  
We specify the relation name and a list of values for the tupl.
Values are listed in the same order as the attributes were specified in `CREATE TABLE`.
User may specify explicit attribute names. The attributes not included cannot have the `NOT NULL` constraint.

## `DELETE`
Used to remove existing tuples from a relation.
A single statement may delete 0 up to all tuples form a table.

## `UPDATE`
Used to modify attribute values o one or more selected tuples in a relation.
Example:  
```sql
UPDATE someTable SET expression WHERE conditional expression
```
## `SELECT`
Basic syntax:  

```sql
SELECT <attribute list> FROM <table list> [WHERE condition]
```

# Projection and selection
Projection is choosing which columns (expressions) will return.
Selection means which rows are to be returned.

# Aggregation and Grouping


