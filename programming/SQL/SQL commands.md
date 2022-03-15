[[SQL]]

Glossary of commonly used SQL commands.

## Background

SQL, **S**tructured **Q**uery **L**anguage, is a programming language designed to manage data stored in relational databases. SQL operates through simple, declarative statements. This keeps data accurate and secure, and it helps maintain the integrity of databases, regardless of size.

Here’s an appendix of commonly used commands.

## Commands

### ALTER TABLE

![[Pasted image 20220222003652.png]]

`ALTER TABLE` lets you add columns to a table in a database.

### AND

![[Pasted image 20220222003802.png]]

`AND` is an operator that combines two conditions. Both conditions must be true for the row to be included in the result set.

### AS

![[Pasted image 20220222003856.png]]

`AS` is a keyword in SQL that allows you to rename a column or table using an _alias_.

### AVG()

![[Pasted image 20220222003928.png]]

`AVG()` is an aggregate function that returns the average value for a numeric column.

### BETWEEN

![[Pasted image 20220222003952.png]]

The `BETWEEN` operator is used to filter the result set within a certain range. The values can be numbers, text or dates.

### CASE

![[Pasted image 20220222004016.png]]

`CASE` statements are used to create different outputs (usually in the `SELECT` statement). It is SQL’s way of handling if-then logic.

### COUNT()

![[Pasted image 20220222004035.png]]

`COUNT()` is a function that takes the name of a column as an argument and counts the number of rows where the column is not `NULL`.

### CREATE TABLE

![[Pasted image 20220222004059.png]]

`CREATE TABLE` creates a new table in the database. It allows you to specify the name of the table and the name of each column in the table.

### DELETE

![[Pasted image 20220222004120.png]]

`DELETE` statements are used to remove rows from a table.

### GROUP BY

![[Pasted image 20220222004136.png]]

`GROUP BY` is a clause in SQL that is only used with aggregate functions. It is used in collaboration with the `SELECT` statement to arrange identical data into groups.

### HAVING

![[Pasted image 20220222004150.png]]

`HAVING` was added to SQL because the `WHERE` keyword could not be used with aggregate functions.

### INNER JOIN

![[Pasted image 20220222004223.png]]

An inner join will combine rows from different tables if the _join condition_ is true.

### INSERT

![[Pasted image 20220222004248.png]]

`INSERT` statements are used to add a new row to a table.

### IS NULL / IS NOT NULL

![[Pasted image 20220222004305.png]]

`IS NULL` and `IS NOT NULL` are operators used with the `WHERE` clause to test for empty values.

### LIKE

![[Pasted image 20220222004326.png]]

`LIKE` is a special operator used with the `WHERE` clause to search for a specific pattern in a column.

### LIMIT

![[Pasted image 20220222004341.png]]

`LIMIT` is a clause that lets you specify the maximum number of rows the result set will have.

### MAX()

![[Pasted image 20220222004408.png]]

`MAX()` is a function that takes the name of a column as an argument and returns the largest value in that column.

### MIN()

![[Pasted image 20220222004425.png]]

`MIN()` is a function that takes the name of a column as an argument and returns the smallest value in that column.

### OR

![[Pasted image 20220222004443.png]]

`OR` is an operator that filters the result set to only include rows where either condition is true.

### ORDER BY

![[Pasted image 20220222004459.png]]

`ORDER BY` is a clause that indicates you want to sort the result set by a particular column either alphabetically or numerically.

### OUTER JOIN

![[Pasted image 20220222004517.png]]

An outer join will combine rows from different tables even if the join condition is not met. Every row in the _left_ table is returned in the result set, and if the join condition is not met, then `NULL` values are used to fill in the columns from the _right_ table.

### ROUND()

![[Pasted image 20220222004533.png]]

`ROUND()` is a function that takes a column name and an integer as arguments. It rounds the values in the column to the number of decimal places specified by the integer.

### SELECT

![[Pasted image 20220222004550.png]]

`SELECT` statements are used to fetch data from a database. Every query will begin with `SELECT`.

### SELECT DISTINCT

![[Pasted image 20220222004605.png]]

`SELECT DISTINCT` specifies that the statement is going to be a query that returns unique values in the specified column(s).

### SUM

![[Pasted image 20220222004624.png]]

`SUM()` is a function that takes the name of a column as an argument and returns the sum of all the values in that column.

### UPDATE

![[Pasted image 20220222004641.png]]

`UPDATE` statements allow you to edit rows in a table.

### WHERE

![[Pasted image 20220222004658.png]]

`WHERE` is a clause that indicates you want to filter the result set to include only rows where the following _condition_ is true.

### WITH

![[Pasted image 20220222004715.png]]

`WITH` clause lets you store the result of a query in a temporary table using an alias. You can also define multiple temporary tables using a comma and with one instance of the `WITH` keyword.

The `WITH` clause is also known as common table expression (CTE) and subquery factoring.