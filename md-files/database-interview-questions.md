# Database Interview Questions

## Common Questions :
#### 1. What is database ?
Database is a collection of organized data that stores any type of data including numbers, string and files. </br>
It uses the DBMS to store, retrieve and update data in a database.</br></br>
<b>Types of databases:</b></br>
* Relational Database </br>
* NoSQL database </br>
* Object-oriented database

#### 2. Explain about relational databases ?
A relational database stores data in tables with rows and columns. Each table can contains primary and foriegn keys.
Tables can be linked through the foreign keys which helps to retrieve related data efficiently. 
Relational databases are preffered when storing and retrieving structured data that has relationships.

#### 3. Explain about NoSQL databases ?
NoSQL databases are designed for handling large amounts of unstructured data.  Unlike relational databases, they don’t use tables with rows and columns. 
Instead, they store data in various formats, like documents, key-value pairs, or graphs

#### 4. What is transactions in database ?
The transactions is series of the operations performed with in the database. All the operations must be completed successfully; if not, the transaction is rolled back to keep the database correct.</br>
```SQL
BEGIN TRANSACTION;

-- Deduct $100 from the checking account
UPDATE accounts
SET balance = balance - 100
WHERE account_type = 'checking' AND account_id = 1;

-- Add $100 to the savings account
UPDATE accounts
SET balance = balance + 100
WHERE account_type = 'savings' AND account_id = 2;

-- If both operations are successful, commit the transaction
COMMIT;

-- If something goes wrong, rollback the transaction to undo changes
ROLLBACK;
```

#### 5. Explain about ACID property ?
The ACID properties ensure that database transactions are processed reliably.</br>
* <b>Atomicity:</b> A transaction happens completely or not at all. </br>
* <b>Consistency:</b> A transaction keeps the database in a correct state.</br>
* <b>Isolation:</b> Transactions don’t interfere with each other.</br>
* <b>Durability:</b> Once a transaction is finished, its changes are permanent, even if there’s a failure.

## SQL

#### 1. What is SQL ?
SQL stands for Structured Query Language that is used to store, retrieve and manipulate data in relational databases. 
SQL is used to create, update, and remove information from a database. It is a query language for relational databases which stores data in tables with rows and columns.

#### 2. Explain the components of sql ?
* <b>DDL (Data Definition Language):</b>Used to create or modify the structure of a database. Ex. `CREATE, ALTER, DROP, TRUNCATE`.</br>
* <b>DML (Data Manipulation Language):</b>Used to create or modify the data in the tables. Ex `SELECT, INSERT, UPDATE, DELETE`.</br>
* <b>DQL (Data Query Language):</b>Used to fetch the data from the database. Ex `SELECT`.</br>
* <b>DCL (Data Control Language):</b>Used to Manages permissions. It controls who can access or modify the data. Ex `GRANT, REVOKE`</br>
* <b>TCL (Transaction Control Language):</b>Used for managing transactions within the database. Ex `COMMIT, ROLLBACK, SAVEPOINT`.

#### 3. What is a primary key ?
A primary key is a unique identifier for each row in a table. It ensures that each record can be uniquely identified.

#### 4. What is a foreign key ?
A foreign key is a column or set of columns in one table that links to the primary key of another table. It establishes a relationship between the two tables.

#### 5. What is normalization ?
Normalization is a process that organizes data in a database to reduce redundancy and improve data integrity. 
It is a process that removes duplicate data from relational tables.</br>

<b>First Normal Form (1NF):</b>  This means each column has only one value per row instead group of values.</br>
<b>Second Normal Form (2NF):</b> Make sure every non-key column depends on the entire primary key, not just part of it.</br>
<b>Third Normal Form (3NF):</b>  Make sure that all columns depend only on the primary key, not on other columns.</br>
<b>Boyce-Codd Normal Form (BCNF):</b>  column or set of columns that determines the value of another column.</br>
<b>Fourth Normal Form (4NF):</b> Ensure that a table has no multi-valued dependencies, meaning a table should not have two or more independent sets of multi-valued data.</br>
<b>Fifth Normal Form (5NF):</b>A table should be designed so that you can reconstruct it by joining smaller, simpler tables without losing any information.

#### 6. What is indexing in SQL ?
Indexing is a process used to speed up the retrieval of data from a database. We can do indexing for both single and multiple columns.</br>
<b>Single Column Index:</b> `CREATE INDEX idx_column_name ON table_name (column_name);`</br>
<b>Multi Column Index:</b> `CREATE INDEX idx_multi_column ON table_name (column1, column2);`

#### 7. What is JOIN ?
A JOIN is used to combine rows from two or more tables based on a related column between them.</br>
* <b>INNER JOIN:</b> Returns rows where there is a match in both tables.</br>
* <b>LEFT JOIN (or LEFT OUTER JOIN):</b> Returns all rows from the left table and matched rows from the right table. If there is no match, NULLs are returned for columns from the right table.</br>
* <b>RIGHT JOIN (or RIGHT OUTER JOIN):</b> Returns all rows from the right table and matched rows from the left table. If there is no match, NULLs are returned for columns from the left table.</br>
* <b>FULL JOIN (or FULL OUTER JOIN): </b> Returns all rows when there is a match in one of the tables. If there is no match, NULLs are returned for columns from the table even if there is a no match.</br>
* <b>CROSS JOIN:</b> Returns the Cartesian product of both tables, i.e., all possible combinations of rows from both tables.</br>
* <b>SELF JOIN:</b> A join where a table is joined with itself to compare rows within the same table.

#### 8. What is subquery in SQL ?
A subquery is a query within another query. The outer query is known as the main query, and the inner query is known as a subquery.
Subqueries are on the right side of the comparison operator. A subquery is enclosed in parentheses.</br>
Ex. `SELECT * FROM EMPLOYEE WHERE ID IN (SELECT ID FROM EMPLOYEE WHERE SALARY > 4500);`.  

#### 10. What is the difference between UNION and UNION ALL?
* UNION combines results from two queries and removes duplicate rows.</br>
* UNION ALL combines results from two queries but includes all duplicates.

#### 11. How do you handle NULL values in SQL?
NULL values represent missing or unknown data. You can use functions like `IS NULL`, `IS NOT NULL`, or handle NULLs with `COALESCE` to provide default values.

#### 12. Explain about MySQL Functions ?
SQL functions are like built-in tools that help you manipulate and analyze data in a database.</br></br>
<b>Aggregation Functions:</b></br>
* <b>SUM():</b> Adds up values.
* <b>AVG():</b> Finds the average value.
* <b>COUNT():</b> Counts the number of rows.
* <b>MIN():</b> Returns the minimum value in a set of values.
* <b>MAX():</b> Returns the maximum value in a set of values.

<b>String Functions:</b> String functions in SQL are used to process and manipulate text data.</br>
* <b>CONCAT():</b> Joins strings together.
* <b>SUBSTRING():</b> Extracts part of a string.
* <b>UPPER():</b> Converts text to uppercase.
* <b>LOWER():</b> Converts text to lowercase.
* <b>LENGTH():</b> returns the length of a string
* <b>TRIM():</b> removes leading and trailing spaces from a string.
* <b>REPLACE():</b> replaces occurrences of `old_string` with `new_substring` in a string.
* <b>LEFT()/RIGHT():</b> returns the left/right length characters of a string
* <b>LTRIM()/RTRIM()</b>  removes left/right side spaces from a string.

<b>Date Functions:</b> Date functions in SQL are used to Handle dates and times.</br>
* <b>NOW():</b> Gets the current date and time.
* <b>DATEPART():</b> Extracts a part of a date, like the year or month.
* <b>DATE_FORMAT():</b> Formats a date according to a specified format.
* <b>DATEDIFF():</b> Calculates the difference between two dates.
* <b>DATEADD():</b> Adds a specified interval to a date.
* <b>CURDATE()/CURTIME():</b> returns the current date/time.

<b>Mathematical Functions:</b> Perform mathematical calculations.</br>
* <b>ROUND():</b> Rounds a number to a specified number of decimal places.
* <b>FLOOR():</b> Rounds down to the nearest whole number.
* <b>CEIL()/CEILING():</b> Rounds up to the nearest whole number.
* <b>SQRT():</b> Returns the square root of a number.
* <b>POWER():</b> Raises a number to a specified power.
* <b>SIGN():</b> Returns the sign of a number (positive, negative, or zero).
  
#### 13. What is the GROUP BY condition in SQL ?
The `GROUP BY` clause in SQL is used to group rows that have the same values in specified columns. The GROUP BY statement is used with aggregate functions like `COUNT()`, `MAX()`, `MIN()`, `SUM()` and `AVG()` to group the result set by one or more columns. In a query, the `GROUP BY` clause is placed before the `ORDER BY` and `HAVING` clauses, if they are used.





