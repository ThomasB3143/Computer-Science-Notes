Section: [[Year 1/Computer Systems/Databases/Databases (Root)]]

SQL (Structured Query Language) is the most common database language. It uses simple syntax and contains two components:

1. Data Definition Language (DDL)
	- Define the attributes for each relation
	- Define the domain of each attribute (their type)
	- Define constraints (primary key/foreign key/not NULL etc)
2. Data Manipulation language (DML)
	- Insert/update/delete/retrieve data from the database
	- Querying the database to retrieve data
## SQL Statements

These consist of:

- Reserved words
	- Fixed parts of SQL
	- SELECT, WHERE, IS NOT NULL operators
- User-Defined Words
	- Names specified by the user
	- Relations
	- Attributes
- Literals
	- Non-numeric literals enclosed in **single quotes** like 'Thomas Blair'
	- Numeric literals left as-is

Here is a great example. It retrieves the first and last name of all staff that are not an assistant and have a salary exceeding £10000:

```
SELECT fName, lName
FROM Staff
WHERE Staff.position != 'Assistant' AND Staff.salary > 10000
```

Note that statements may be chained and terminated through use of a semicolon
## Data Manipulation Language (DML)

The main statements of this area include:

- SELECT - Query data in the database
- INSERT - Insert new records into an existing table
- UPDATE - To update records in an existing table
- DELETE - To delete records from an existing table
### SELECT

![[Pasted image 20250401205510.png]]
1. FROM - Specifies the tables being used
2. WHERE - Filters the rows subject to a condition
3. GROUP BY - Forms groups of rows with the same value
4. HAVING - Filters group subject to a condition
5. SELECT - Specifies which columns are to appear in the output
6. ORDER BY - Specifies the order of output

Note that in the SELECT portion, * can be used to select every column in all tables referenced in the FROM portion
![[Pasted image 20250401205838.png]]
In the SELECT statement we can derive attributes and assign them new names in our output. You CANNOT use the new name anywhere in the rest of the SQL statement. The use of DISTINCT will eliminate rows containing duplicates of a cell
#### WHERE

Here is a handy cheat sheet for conditions in our WHERE portion:
![[Pasted image 20250401210104.png]]For pattern-matching, SQL uses two symbols. A "%" represents a **sequence** of characters, whereas a " _ " represents a single character. You can even use NOT LIKE instead of LIKE 
#### ORDER BY

ORDER BY can sort the outputted rows in ascending or descending relative to a certain attribute
#### Aggregate Functions

These operate on a single attribute, taking each cell and returning a single value. We have:

| Function | What it does                                                  |
| -------- | ------------------------------------------------------------- |
| SUM      | Sum of the numeric values in a given column                   |
| AVG      | Average value of a given column                               |
| MIN      | Smallest value in a given column                              |
| MAX      | Largest value in a given column                               |
| COUNT    | The total number of values in a given column (Excluding NULL) |
| COUNT(*) | Number of rows in a table (Includes NULL)                     |
#### GROUP BY

GROUP BY is used in combination with aggregate functions. It groups rows by one or more attributes and applies the function to each group separately. Here is a simple example:![[Pasted image 20250401211123.png]]
### INSERT

![[Pasted image 20250401211835.png]]
Note that "columnList" is optional, as if it is not specified then the column are enumerated in the order the table was created. If it **is** specified, then omitted columns are set to NULL
### UPDATE

![[Pasted image 20250401212045.png]]
Note that the dataValue's must be respect the data type of that attribute
### DELETE

![[Pasted image 20250401212237.png]]
Not specifying a condition will delete all rows from the table. This does not delete a table, as for that we would use DROP TABLE
## Data Definition Language (DDL)

Commands in this section are for defining data in the DB:

- CREATE - Creates a new table and defines its schema
- ALTER - Changes the relation schema
- DROP - Deletes an entire table
- CREATE VIEW - Defines a view for a user, derived from a query
### DOMAIN TYPES

Here are some common domain types you should know:

- CHAR(n) - A character string of fixed length n
- VARCHAR(n) - A character string of maximum length n
- BIT(n) - A bit string of length n
- INTEGER - Large positive/negative integer values
- SMALLINT - INTEGER but only up to 32767
- NUMERIC(p,d) a decimal number with at most p digits and d decimal digits

We can even define our own domains types like so:

```
CREATE DOMAIN Postcode AS VARCHAR(8);

CREATE DOMAIN Gender AS CHAR(1)
CHECK (VALUE IN ('M','F','O'));
```

### Integrity and Constraints

We can specify things such as PRIMARY KEY and FOREIGN KEY.

We can also define what to do ON UPDATE or ON DELETE. For this, we have the following:

- CASCADE - When updating/deleting, update the foreign key/delete the tuple
- SET NULL - When updating/deleting, set the foreign key to NULL
- SET DEFAULT - Set the foreign key to a default value
- NO ACTION - Do nothing
### CREATE TABLE

![[Pasted image 20250401214030.png]]

Here is a great example demonstrating all the previously explained features:

![[Pasted image 20250401214118.png]]
### ALTER

This is used to change the schema of a relation in three ways:

- Adding new attributes:
	- ALTER TABLE Person ADD salary INTEGER
- Removing attributes:
	- ALTER TABLE Person DROP married CASCADE
- Change attribute characteristics
	- ALTER TABLE Person ALTER gender SET DEFAULT 'F'
### CREATE VIEW

A view is a table derived from one or more other tables and can be used to present the same information in different ways to different users (to simplify complex queries). Here is how:
![[Pasted image 20250401215026.png]]
## Joins

When we query multiple tables, we need some way to combine them into one result. We can do this by either forming **all combinations** of all rows, or by **appending** one table to the other.

We often want a combination of:

- Combining rows
- Filtering rows
- Appending rows
  
![[Pasted image 20250402142525.png]]
![[Pasted image 20250402142616.png]]
Note that INNER JOIN is identical to using a [[SQL#WHERE|WHERE]] like so:

```
SELECT *
FROM Staff, Branch
WHERE Staff.branchNo = Branch.branchNo
```

However INNER JOIN is much more efficient. The above statement can be rewritten as:

```
SELECT *
FROM Staff JOIN Branch ON Staff.branchNo = Branch.branchNo
```

But you can still use a WHERE when you JOIN, like so:

```
SELECT *
FROM Staff JOIN Branch ON Staff.branchNo = Branch.branchNo
WHERE fName LIKE '____'
```

This will filter out staff to include only those with four-letter first names
## Subqueries

You can reuse the result of a query for another query. But do this you need to know the three different types of return values for a query:

- Single-Value - A single column and single row
- Multi-Value - A single column with multiple rows
- Tabular - Multiple columns and multiple rows