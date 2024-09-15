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

## SQL Query Questions(MySQL)
<b>Part-1: Aggregation Functions</b>
#### 1. find the average salary of the employee ?
```sql
select AVG(salary) from employee;
```
#### 2. find the employees who joined the organization in specific year ?
```sql
select * from employee where year(DOJ) = 2000;
```
#### 3. Find highest salary of employee ?
```sql
select MAX(SALARY) from employee;
```
#### 4. find second or n-th highest salary of employee ?
<b>Without windows function :</b></br>
```sql
SELECT MAX(salary) AS second_highest_salary FROM employees WHERE salary < (SELECT MAX(salary) FROM employees);
```
<b>With windows function :</b></br> 
```sql
SELECT DISTINCT salary AS second_highest_salary FROM employees order by salary DESC LIMIT 1 OFFSET 1;
```
#### 5. How many employees are there in department ?
```sql
select count(emp_no) from employee where DEPT = 'Java';
```
#### 6. Find the average salary of male and female employee ?
```sql
SELECT gender, AVG(SALARY) AS AVG_SALARY FROM EMPLOYEE GROUP BY gender;
```
#### 7. How many male and female employees are there ?
```sql
SELECT gender, COUNT(GENDER) AS count FROM EMPLOYEE GROUP BY gender;
```
#### 8. How many females are there in particular department(JAVA) ?
```sql
select dept, count(*) AS female_count from employee where gender = 'FEMALE' and dept = 'IT' GROUP BY dept;
```
#### 9. Increment the salary of hr department by 10 parcentage ?
```sql
UPDATE EMPLOYEE SET SALARY = SALARY * 1.1 WHERE DEPT = 'HR';
```
#### 10. Find the oldest and youngest employee in organization ?
```sql
SELECT * FROM employees ORDER BY dob ASC LIMIT 1;
SELECT * FROM employees ORDER BY dob DESC LIMIT 1;
```
#### 11. Find minimum and maximum salary of employee ?
```sql
SELECT MIN(salary) AS min_salary, MAX(salary) AS max_salary FROM EMPLOYEE;
```
<b>Part-2: String Functions</b>
#### 1. How do you concatenate two or more strings in SQL ?
```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM EMPLOYEE;
```
#### 2. If some names contain NULL values, how would you modify your CONCAT operation to handle these gracefully ?
```sql
SELECT CONCAT(COALESCE(Firstname, ''), ' ', COALESCE(Lastname, '')) AS full_name FROM employee;
```
#### 3. How do you find the length of a string in SQL ?
```sql
SELECT LENGTH(column_name) AS string_length FROM table_name;
```
#### 4. How do you extract a substring from a string in SQL ?
```sql
SELECT SUBSTRING(column_name, start_position, length) AS extracted_substring FROM table_name;
```
#### 5. How do you convert a string to uppercase or lowercase in SQL ?
```sql
SELECT UPPER(column_name) AS upper_case_string FROM table_name;
SELECT LOWER(column_name) AS lower_case_string FROM table_name;
```
#### 6. How do you trim leading and trailing spaces from a string in SQL ?
```sql
SELECT TRIM(column_name) AS trimmed_string FROM table_name;
```
#### 7. How do you replace a substring within a string in SQL ?
```sql
SELECT REPLACE(column_name, 'old_substring', 'new_substring') AS replaced_string FROM table_name;
```
#### 8. How do you find the position of a substring within a string in SQL ?
```sql
SELECT INSTR(column_name, 'substring') AS position FROM table_name;
```
#### 9. How do you check if a string contains a substring in SQL ?
```sql
SELECT CASE
          WHEN column_name LIKE '%substring%' THEN 'Contains'
          ELSE 'Does not contain'
       END AS contains_substring
FROM table_name;
```
#### 10. How do you pad a string to a certain length with a specific character in MySQL ?
```sql
SELECT LPAD(column_name, length, 'padding_char') AS padded_string FROM table_name;
SELECT RPAD(column_name, length, 'padding_char') AS padded_string FROM table_name;
```
#### 11. How do you split a string by a delimiter in MySQL ?
```sql
SELECT SUBSTRING_INDEX(column_name, 'delimiter', n) AS part FROM table_name;
```
#### 12. Get the first name that starts with 'J' in MySQL?
```sql
#Case-Insensitive
SELECT * FROM employee WHERE firstname LIKE 'J%';
#Case-Sensitive
SELECT * FROM employee WHERE BINARY firstname LIKE 'J%'; 
```
#### 13. Get the first name that ends with 'N' in MySQL?
```sql
#Case-Insensitive
SELECT * FROM employee WHERE firstname LIKE '%N';
#Case-Sensitive
SELECT * FROM employee WHERE BINARY firstname LIKE '%N';
```
#### 14. Get the first name that starts with 'J' and ends With 'N' in MySQL?
```sql
#Case-Insensitive
SELECT * FROM employee WHERE firstname LIKE 'J%N';
#Case-Sensitive
SELECT * FROM employee WHERE BINARY firstname LIKE 'J%N';
```
<b>Part-3: SQL Joins</b>
#### 1. INNER JOIN:
Only the rows where there is a match in both tables.
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```
<b>Example:</b> Get employees and their respective departments (only if they are assigned to a department).
#### 2. LEFT JOIN (LEFT OUTER JOIN):
All rows from the left table and matched rows from the right table. If there's no match, NULL will be returned for the right table.
```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
<b>Example:</b> Get all employees and their departments, even if they are not assigned to one.
####  3. RIGHT JOIN (RIGHT OUTER JOIN):
 All rows from the right table and matched rows from the left table. If there's no match, NULL will be returned for the left table.
 ```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
 ```
<b>Example:</b> Get all departments and their employees, even if there are no employees in a department.
#### 4. FULL OUTER JOIN:
All rows when there is a match in either left or right table. Rows without a match will return NULL on the non-matching side.
```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```
<b>Example:</b> Get all employees and departments, even if they aren't linked to one another.
#### 5. CROSS JOIN:
The Cartesian product of both tables (every row from the first table paired with every row from the second table).
```sql
SELECT columns
FROM table1
CROSS JOIN table2;
```
<b>Example:</b> Get all possible combinations of employees and projects (use carefully as it can create a huge result set).
#### 6. SELF JOIN:
A join of a table to itself. Useful for hierarchical or relational data within the same table.
```sql
SELECT a.column, b.column
FROM table1 a
INNER JOIN table1 b
ON a.column = b.column;
```
<b>Example:</b> Get all employees along with their manager details from the same table.
#### 7. NATURAL JOIN:
A join based on columns with the same name and datatype in both tables (automatically performed).
```sql
SELECT columns
FROM table1
NATURAL JOIN table2;
```
<b>Example:</b> Automatically joins the tables based on matching columns without specifying the ON condition.

<b>Part-4: Date/Time Functions</b>
#### 1. How would you get the current date and time in SQL ?
```sql
SELECT CURRENT_TIMESTAMP;
```
#### 2. How would you extract only the year, month, or day from a date ? 
```sql
SELECT EXTRACT(YEAR FROM NOW()), EXTRACT(MONTH FROM NOW()), EXTRACT(DAY FROM NOW());
```
#### 3. How do you calculate the difference between two dates in days ?
```sql
SELECT DATEDIFF('2024-12-31', '2024-01-01');
```
#### 4. How can you add days, months, or years to a date ?
```sql
SELECT DATE_ADD('2024-09-15', INTERVAL 10 DAY);
SELECT DATE_ADD('2024-09-15', INTERVAL 1 MONTH);
```
#### 5. How do you format a date in a specific format (e.g., YYYY-MM-DD) ?
```sql
SELECT DATE_FORMAT(NOW(), '%Y-%m-%d');
```
#### 6. Write a query to return all employees who joined in the last 30 days ?
```sql
SELECT * FROM employees WHERE join_date >= DATE_SUB(CURDATE(), INTERVAL 30 DAY);
```
#### 7. Get All Employees Who Have a Birthday This Month ?
Fetch a list of employees whose birthday occurs in the current month, regardless of the year.
```sql
SELECT employee_id, name, birth_date
FROM employees
WHERE MONTH(birth_date) = MONTH(CURDATE());
```
#### 8. Calculate the Age of Each Employee ?
Calculate the age of employees from their date of birth.
```sql
SELECT employee_id, name, 
   FLOOR(DATEDIFF(CURDATE(), birth_date) / 365) AS age
FROM employees;
```
#### 9. Find the Difference Between Two Date Columns in Different Units (Years, Months, Days) ?
Calculate the difference between the start_date and end_date in different units.
```sql
SELECT employee_id, 
   TIMESTAMPDIFF(YEAR, start_date, end_date) AS years_diff,
   TIMESTAMPDIFF(MONTH, start_date, end_date) AS months_diff,
   TIMESTAMPDIFF(DAY, start_date, end_date) AS days_diff
FROM employees_projects;
```
#### 10. Get All Orders Made in the Last 7 Days ?
Retrieve all the orders that were placed in the last 7 days (a rolling window from the current date).
```sql
SELECT order_id, order_date, customer_id
FROM orders
WHERE order_date >= DATE_SUB(CURDATE(), INTERVAL 7 DAY);
```
#### 11. Find Employees Who Have Been With the Company for More Than 5 Years ?
Fetch employees whose hire_date is more than 5 years ago.
```sql
SELECT employee_id, name, hire_date
FROM employees
WHERE hire_date <= DATE_SUB(CURDATE(), INTERVAL 5 YEAR);
```
#### 12. Calculate Total Time Spent on Projects by Each Employee ?
For each employee, calculate the total time (in days) they’ve worked across different projects.
```sql
SELECT employee_id, name, 
   SUM(DATEDIFF(end_date, start_date)) AS total_days_worked
FROM employees_projects
GROUP BY employee_id;
```
#### 13. Get the First and Last Order Date for Each Customer ?
Retrieve the first and last order dates for each customer.
```sql
SELECT customer_id, 
   MIN(order_date) AS first_order, 
   MAX(order_date) AS last_order
FROM orders
GROUP BY customer_id;
```
#### 14. Get Employees with Ongoing Projects (Start Date in the Past and No End Date) ?
Find employees working on projects that are ongoing, meaning they have a start date but no end date (i.e., end_date is NULL).
```sql
SELECT employee_id, project_id, start_date
FROM employees_projects
WHERE start_date <= CURDATE() AND end_date IS NULL;
```
#### 15. Find Customers Who Have Not Placed Orders in the Last Year ?
Identify customers who have not placed an order in the last year.
```sql
SELECT customer_id, name
FROM customers
WHERE customer_id NOT IN (
   SELECT customer_id
   FROM orders
   WHERE order_date >= DATE_SUB(CURDATE(), INTERVAL 1 YEAR)
);
```
#### 16. Get Sales Data Grouped by Month and Year ?
Retrieve total sales for each month and year, grouped and ordered accordingly.
```sql
SELECT 
   YEAR(order_date) AS year, 
   MONTH(order_date) AS month, 
   SUM(total_amount) AS total_sales
FROM sales
GROUP BY YEAR(order_date), MONTH(order_date)
ORDER BY YEAR(order_date), MONTH(order_date);
```
#### 17. Find the Number of Orders Each Day for the Last 30 Days ?
Calculate how many orders were placed each day in the last 30 days.
```sql
SELECT order_date, COUNT(*) AS total_orders
FROM orders
WHERE order_date >= DATE_SUB(CURDATE(), INTERVAL 30 DAY)
GROUP BY order_date
ORDER BY order_date;
```
## MongoDB 
#### 1. What is MongoDB ?
MongoDB is a NoSQL database that stores data in a flexible, JSON-like format called BSON. Unlike traditional databases that use tables and rows, MongoDB uses collections and documents, allowing you to handle large amounts of unstructured data more easily.

#### 2. What is the difference between MongoDB and MySQL ?
MySQL is a relational database that uses structured tables with rows and columns.</br> 
MongoDB is a NoSQL database that stores data in flexible, JSON-like documents.

#### 3. How does MongoDB handle indexing ?
MongoDB uses indexes to quickly find documents in a collection. Without indexes, MongoDB searches every document, which is slow.
An index lets MongoDB find data faster by jumping to the right documents instead of scanning everything.

#### 4. What is an Aggregation Framework in MongoDB ?
The Aggregation Framework in MongoDB is a powerful tool for processing and analyzing data. It supports operations such as filtering, grouping, and sorting the data. Key components of MongoDB's aggregation methods include:
* $match: Filters documents based on criteria (similar to a WHERE clause).
* $group: Groups documents by a specified field and performs aggregation operations like sum or average.
* $sort: Sorts documents based on specified fields.
* $project: Reshapes documents by including or excluding fields.
* $limit: Limits the number of documents returned.
* $skip: Skips a specified number of documents.
* $lookup: Performs a left join to include documents from another collection.
* $unwind: Deconstructs an array field from documents to output a document for each element.

#### 5. What is a Replica Set in MongoDB ?
A Replica Set in MongoDB is a group of MongoDB servers that work together to ensure data is always available. One server is the primary where all writes happen, while the others are secondaries that copy the data from the primary. If the primary server fails, one of the backup servers automatically becomes the new primary, so the data remains available and safe.

#### 6. How do you handle pagination in MongoDB ?
To handle pagination in MongoDB, use the $skip and $limit stages in the aggregation pipeline or directly in the query.

* $skip: Skips a number of documents based on the current page.
* $limit: Limits the number of documents returned to show on that page.


## MongoDB Query Questions
#### 1. How do you retrieve all documents from a MongoDB collection ?
To retrieve all documents from a MongoDB collection, use the find() method without any query parameters.
```javascript
db.collection.find();
```
#### 2. How do you find documents where a field equals a specific value ?
To find documents where a specific field matches a value, use the find() method with a query object.
```javascript
db.collection.find({ field: "value" });
```
#### 3. How do you insert a single document into a MongoDB collection ?
To insert a single document, use the insertOne() method.
```javascript
db.collection.insertOne({
  name: "John Doe",
  age: 30,
  email: "john.doe@example.com"
});
```
#### 4. How do you insert multiple documents into a MongoDB collection ?
To insert multiple documents, use the insertMany() method.
```javascript
db.collection.insertMany([
  { name: "Alice Smith", age: 25, email: "alice.smith@example.com" },
  { name: "Bob Johnson", age: 40, email: "bob.johnson@example.com" }
]);
```
#### 5. How do you update a single document in a MongoDB collection ?
To update a single document, use the updateOne() method:.
```javascript
db.collection.updateOne(
  { field: "value" }, // Query filter
  { $set: { fieldToUpdate: "newValue" } } // Update operation
);
```
#### 6. How do you delete a document from a MongoDB collection ?
To delete a single document, use the deleteOne() method.
```javascript
db.collection.deleteOne({ field: "value" });
```
#### 7. How do you count the number of documents in a MongoDB collection ?
To count the number of documents in a collection, use the countDocuments() method.
```javascript
db.collection.countDocuments(); // total number of documents in the collection.
db.collection.countDocuments({ field: "value" }); // query filter to count only documents that match certain criteria:
```
#### 8. How do you sort documents by a specific field in MongoDB ?
To sort documents by a specific field, use the sort() method with a sort order.
```javascript
db.collection.find().sort({ field: 1 }); // Ascending order
db.collection.find().sort({ field: -1 }); // Descending order
```
#### 9. How do you find documents where a field’s value is greater than a specific value ?
To find documents where a field’s value is greater than a specific value, use a comparison operator.
```javascript
db.collection.find({ field: { $gt: value } });
```
#### 10. How do you find documents where a field’s value is within a specific range ?
To find documents where a field’s value is within a range, use the $gte (greater than or equal to) and $lte (less than or equal to) operators.
```javascript
db.collection.find({ field: { $gte: minValue, $lte: maxValue } });
```
#### 11. How do you perform a partial text search(Reg Exp) in MongoDB ?
To perform a partial text search, use regular expressions.
```javascript
db.collection.find({ field: /pattern/ });
```
#### 12. How do you perform pagination in MongoDB ?
To handle pagination in MongoDB, use the $skip and $limit stages in the aggregation pipeline or directly in the query.
```javascript
db.items.find()
  .skip(10)  // Skip the first 10 items (for page 1)
  .limit(10) // Limit the results to 10 items (for page 2)
```





