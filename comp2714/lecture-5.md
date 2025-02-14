continue SQL
==

# Aggregation and Grouping
Aggregates are functions that produce summary values from a set of tuples.
They can be applied to 
* all tuples
* a selected set of tuples
* multiple groups of tuples specified by `GROUP BY`

Aggregation function can be used in the `SELECT` clause
and the `HAVING` clause.

## Funcitons
* `COUNT`: conuts the number of tuples that the query returns
* `SUM/AVG`: calculate the sum or average of numeric values
* `MAX/MIN`

They can be used with distinct.

**Examples**:  
```mysql
SELECT AVG(salary) as 'ave_salary', SUM(salary) as 'sum_salary'
    FROM Employee;

SELECT COUNT(*)
    FROM Employee
    WHERE dNum = 5;

SELECT COUNT(DISTINCT salary) /* how many distinct salary values are there? */
    FROM Employee
    WHERE dNum = 5; /* we can use this to find duplicates! */
```

## `GROUP BY`
When group by is used, any attribute which appears in the select clause must also appear in the group by clause or be in an aggregation function.
```mysql
SELECT [DISTINCT] target_list
FROM table_list
[WHERE []]
[GROUP BY []]
[HAVING ]
[ORDER BY [] ASC | DESC]
```

**Example**:
```mysql
SELECT dNum, COUNT(*)
    FROM Employee
    WHERE salary > 40000
    GROUP BY dNum;
```
Any attribute which appears in `SELECT` must either appeare in `GROUP BY` or it must be an aggregate function.

## `HAVING`
Conditions can be imposed on the selection of groups to be included in the query result.
With `HAVING`, we can use aggregate functions. 
```mysql
SELECT * 
    FROM Employee
    HAVING salary = MIN(salary);

/* is equivalent to */

SELECT *
    FROM Employee
    WHERE salary = 
        (SELECT min(salary)
            FROM Employee);
```

It's basically for filtering aggregate results.
attributes in `HAVING` must either be in `GROUP BY` or an aggregate function.

# Multiple Relation SQL Query

## Renaming
```mysql
SELECT E.name, salary, 1.17 * salary as 'includingSuper'
    FROM Employee AS E
    WHERE dNum = 4;
```

# Joins
A join is used to combine related tuples from two relations into a single tuple in a new resulting relation.
Join operation is needed for organising a search space of data.

# Cartesian Product
```math
R_{1} \times R_{2}
```

Every row in $R\_1$ is combined with every row in $R\_2$.

```mysql
SELECT *
    FROM MovieStar, StarsIn
```

# EQUI-JOIN
Joins tupels from two relations when they have the same value for some pairs of designated attributes. The specification is termed a "join condition".

With equi-join, the join condition only has equality comparisons.

**Example**:  
```mysql
SELECT A, R1.B, C
    FROM R1, R2
    WHERE R1.B = R2.B;
```
The condition does not need to be an equality.
It could also be a greater-than/less-than condition as well.

# THETA-JOIN
An theta-join is a more general form of the equi-join.
It can include other comparison operators.
