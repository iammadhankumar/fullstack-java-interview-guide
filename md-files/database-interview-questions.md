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



