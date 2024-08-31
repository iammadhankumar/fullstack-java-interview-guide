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
