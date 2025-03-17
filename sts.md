### 1. What are the features of java 17 ?
#### <b>Sealed Classes:</b> </br>
Sealed classes in Java (introduced in Java 15 and finalized in Java 17) restrict which classes can inherit from them. 
The permits keyword specifies the allowed subclasses. This ensures better code organization, security, and maintainability by preventing unwanted extensions.</br>

  <b>Uses:</b>
* <b>Ensuring Security:</b> Prevents unauthorized subclasses that could modify behavior.
* <b>Better Maintainability:</b> Limits extension to known classes, making code easier to manage.
* <b>Clearer Design:</b> Defines a strict hierarchy, avoiding unintended modifications.
* <b>Improved Performance:</b> Helps compilers optimize code by knowing the exact class hierarchy.
  
#### <b>Pattern Matching for Switch:</b> </br>
Pattern Matching for switch (introduced in Java 17 as a preview and finalized in Java 21) allows matching values based on their type, making switch statements more readable and type-safe.</br>
It eliminates the need for explicit casting and instanceof checks.

```java
static String typeCheck(Object obj) {
    return switch (obj) {
        case String s -> "String: " + s;
        case Integer i -> "Integer: " + i;
        default -> "Unknown type";
    };
}
```
#### <b>New RandomGenerator API:</b>
The New RandomGenerator API (introduced in Java 17) provides a more flexible and powerful way to generate random numbers.
It includes multiple implementations like L128X128MixRandom, L64X128MixRandom, and SplittableRandom, offering better performance and predictability.

```java
RandomGenerator random = RandomGenerator.of("L128X128MixRandom");
int num = random.nextInt(100);  
System.out.println(num);
```
Apart from this, Java 17 improves performance and security with better Garbage Collection (ZGC & G1), stricter encapsulation of JDK internals, native Apple Silicon support
and the deprecation of outdated features like SecurityManager and RMI Activation. 🚀

### 2. Do you have experience in GCP ?
I haven't worked directly with GCP, but I have strong experience in AWS (or Azure), particularly in services like EC2, S3, Lambda, and IAM. 
Since cloud platforms share many fundamental concepts, I believe I can quickly adapt to GCP.
Additionally, I have a strong foundation in cloud computing principles, and I am eager to explore GCP further.
* <b>What is Google Cloud Platform (GCP)?</b></br>
   GCP is a cloud computing platform that provides infrastructure, storage, networking, and AI/ML services.
* <b>How is GCP different from AWS and Azure?</b></br>
  GCP focuses on high-performance networking, AI/ML capabilities, and cost-effective compute options, whereas AWS is more enterprise-driven, and Azure integrates well with Microsoft products.
* <b>What are the core components of GCP?</b></br>
 The core components are Compute (VMs, Kubernetes), Storage (Cloud Storage, BigQuery), Networking (VPC, Load Balancer), Security (IAM, Cloud KMS), and AI/ML (Vertex AI, AutoML).
* <b>What are the different compute options in GCP?</b></br>
 GCP offers Compute Engine (VMs), Kubernetes Engine (GKE), Cloud Run (Serverless), and App Engine (PaaS for web apps).

### 3. Deploying Java Application on GCP ? 
You can deploy the Java application on GCP using:

* Google Compute Engine (VMs) – Deploy as a traditional server-based app.
* Google Kubernetes Engine (GKE) – Deploy as a containerized application using Docker.
* App Engine (PaaS) – Deploy a Spring Boot/Maven-based app without managing infrastructure.
  
### 4.  How to set Up GCP SDK & Authentication ?
*  Install Google Cloud SDK.
*  Create a service account with required roles (IAM -> ADMIN -> Service Account).
*  Download the JSON key file and set the env variable.

### 4. How pub/sub differnt from kafka ?
  * Google Pub/Sub is a Google-managed messaging service that automatically scales and is easy to set up.
  * Kafka is a self-managed system that requires setup and handles large amounts of real-time data efficiently.

    # PostgreSQL Interview Questions and Answers

## 1. What is PostgreSQL, and how does it differ from other databases like MySQL?
PostgreSQL is an open-source, object-relational database known for its robustness, extensibility, and support for complex queries.

### Differences from MySQL:
- PostgreSQL supports advanced features like JSONB, full-text search, and window functions.
- It follows strict ACID compliance, whereas MySQL (with some storage engines) may not.
- PostgreSQL supports more advanced indexing and concurrency control.

---

## 2. How do you create a database in PostgreSQL?
Run the following command in the PostgreSQL shell:
```sql
CREATE DATABASE mydatabase;
```
Or use `psql`:
```bash
createdb mydatabase
```

---

## 3. What are some key features of PostgreSQL?
- **ACID compliance** for reliable transactions  
- **Advanced indexing** (B-tree, Hash, GIN, GiST)  
- **JSON and JSONB support** for semi-structured data  
- **Full-text search capability**  
- **Extensibility** (custom functions, data types, operators)  
- **Multi-version concurrency control (MVCC)**  

---

## 4. Explain the difference between `CHAR`, `VARCHAR`, and `TEXT` data types in PostgreSQL.
- `CHAR(n)`: Fixed-length string, always occupies `n` characters.
- `VARCHAR(n)`: Variable-length string, limited to `n` characters.
- `TEXT`: Variable-length string with no character limit.

Use `TEXT` when you don’t need a length constraint.

---

## 5. How do you list all databases in PostgreSQL?
In `psql`, run:
```sql
\l
```
Or use SQL:
```sql
SELECT datname FROM pg_database;
```

---

## 6. How do you switch between databases in PostgreSQL?
In `psql`, use:
```sql
\c mydatabase
```
Or in SQL:
```sql
USE mydatabase;  -- Not supported in PostgreSQL
```
You must reconnect using `psql -d mydatabase` from the terminal.

---

## 7. How do you create a table in PostgreSQL?
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(255) UNIQUE
);
```

---

## 8. What are some commonly used PostgreSQL data types?
- **Numeric:** `INTEGER`, `BIGINT`, `DECIMAL`, `NUMERIC`  
- **Character:** `CHAR`, `VARCHAR`, `TEXT`  
- **Date & Time:** `DATE`, `TIMESTAMP`, `TIME`, `INTERVAL`  
- **Boolean:** `BOOLEAN`  
- **JSON:** `JSON`, `JSONB`  

---

## 9. How do you insert, update, and delete data in PostgreSQL?
### Insert:
```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john@example.com');
```
### Update:
```sql
UPDATE users SET email = 'john.doe@example.com' WHERE name = 'John Doe';
```
### Delete:
```sql
DELETE FROM users WHERE name = 'John Doe';
```

---

## 10. How do you retrieve all records from a table?
```sql
SELECT * FROM users;
```

---

# PostgreSQL Intermediate Interview Questions and Answers

## 1. What is a primary key in PostgreSQL?
A **primary key** is a column (or set of columns) that uniquely identifies each row in a table. It automatically creates a unique index and does not allow `NULL` values.

### Example:
```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);
```

---

## 2. Explain the difference between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN in PostgreSQL.

- **INNER JOIN**: Returns matching rows from both tables.
- **LEFT JOIN**: Returns all rows from the left table and matching rows from the right table.
- **RIGHT JOIN**: Returns all rows from the right table and matching rows from the left table.
- **FULL JOIN**: Returns all rows from both tables, with `NULL` for non-matching rows.

### Example:
```sql
SELECT employees.id, employees.name, departments.name 
FROM employees 
INNER JOIN departments ON employees.dept_id = departments.id;
```

---

## 3. How do you create an index in PostgreSQL, and why is it useful?
An **index** improves query performance by allowing faster searches.

### Example:
```sql
CREATE INDEX idx_employee_name ON employees(name);
```
Indexes speed up `SELECT` queries but may slow down `INSERT`, `UPDATE`, and `DELETE` operations.

---

## 4. What is the difference between a unique constraint and a primary key?
- **Primary Key**: Ensures uniqueness and does not allow `NULL` values.
- **Unique Constraint**: Ensures uniqueness but allows `NULL` values.

### Example:
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE
);
```

---

## 5. How does PostgreSQL handle transactions, and what are ACID properties?
Transactions in PostgreSQL ensure **ACID** properties:

- **Atomicity**: All operations succeed or none do.
- **Consistency**: The database remains valid before and after transactions.
- **Isolation**: Transactions do not interfere with each other.
- **Durability**: Changes are saved permanently.

### Example:
```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

---

## 6. How do you use sequences in PostgreSQL?
A **sequence** generates unique numbers, often used for primary keys.

### Example:
```sql
CREATE SEQUENCE order_seq START 1;
SELECT nextval('order_seq');
```
Using it in a table:
```sql
CREATE TABLE orders (
    id INTEGER DEFAULT nextval('order_seq') PRIMARY KEY,
    product VARCHAR(100)
);
```

---

## 7. Explain the difference between NOW(), CURRENT_TIMESTAMP, and LOCALTIMESTAMP.
- **NOW()**: Returns the current timestamp with time zone.
- **CURRENT_TIMESTAMP**: Same as `NOW()`, returns the timestamp with time zone.
- **LOCALTIMESTAMP**: Returns the current timestamp without time zone.

### Example:
```sql
SELECT NOW(), CURRENT_TIMESTAMP, LOCALTIMESTAMP;
```

---

## 8. What is a foreign key constraint, and how is it used?
A **foreign key** enforces a relationship between two tables, ensuring that the referenced value exists.

### Example:
```sql
CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id)
);
```
This ensures that `user_id` in `orders` must exist in the `users` table.

---

## 9. How do you handle case sensitivity in PostgreSQL queries?
PostgreSQL is case-sensitive for string comparisons. To perform case-insensitive queries, use `ILIKE` or `LOWER()`.

### Example:
```sql
SELECT * FROM users WHERE LOWER(name) = LOWER('John');
```
Or:
```sql
SELECT * FROM users WHERE name ILIKE 'john';
```

---

## 10. How can you optimize a slow query in PostgreSQL?
- Use **Indexes**:  
  ```sql
  CREATE INDEX idx_name ON users(name);
  ```
- Analyze Query Performance:
  ```sql
  EXPLAIN ANALYZE SELECT * FROM users WHERE name = 'John';
  ```
- Optimize Joins using proper indexing.
- Use **VACUUM ANALYZE** to optimize table performance:
  ```sql
  VACUUM ANALYZE;
  ```

---

# PostgreSQL Advanced Interview Questions and Answers

## 1. Explain the concept of table partitioning in PostgreSQL.
**Table partitioning** splits a large table into smaller, more manageable pieces called partitions. It improves query performance by reducing the amount of scanned data.

### Example:
```sql
CREATE TABLE sales (
    id SERIAL PRIMARY KEY,
    sale_date DATE NOT NULL,
    amount NUMERIC
) PARTITION BY RANGE (sale_date);
```

Then, create partitions:
```sql
CREATE TABLE sales_2024 PARTITION OF sales FOR VALUES FROM ('2024-01-01') TO ('2025-01-01');
```

---

## 2. What are CTEs (Common Table Expressions), and how do they work?
A **Common Table Expression (CTE)** is a temporary result set used within a query. It improves query readability and avoids subqueries.

### Example:
```sql
WITH top_sales AS (
    SELECT name, amount FROM sales ORDER BY amount DESC LIMIT 5
)
SELECT * FROM top_sales;
```
CTEs help in breaking down complex queries into simpler parts.

---

## 3. What are JSON and JSONB data types in PostgreSQL, and when should you use them?
- **JSON**: Stores data as text (slower for queries).  
- **JSONB**: Stores data in binary format (faster for queries and indexing).  

Use **JSONB** when you need indexing and frequent querying.

### Example:
```sql
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    details JSONB
);
```
Insert JSON data:
```sql
INSERT INTO products (details) VALUES ('{"name": "Laptop", "price": 1000}');
```

Query JSONB:
```sql
SELECT details->>'name' FROM products;
```

---

## 4. How does PostgreSQL handle concurrency control?
PostgreSQL uses **MVCC (Multi-Version Concurrency Control)** to allow multiple transactions without locking.

- **READ COMMITTED**: Default mode; each query sees only committed data.
- **REPEATABLE READ**: Ensures queries in the same transaction see a consistent snapshot.
- **SERIALIZABLE**: Ensures full isolation but may cause rollbacks.

### Example:
```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```
MVCC ensures transactions don’t block each other.

---

## 5. How do you perform full-text search in PostgreSQL?
Full-text search allows searching within text columns.

### Example:
```sql
SELECT * FROM articles WHERE to_tsvector(content) @@ to_tsquery('PostgreSQL & tutorial');
```

To create an index for faster search:
```sql
CREATE INDEX idx_articles_search ON articles USING GIN (to_tsvector('english', content));
```
This makes text searches faster.

---

## 6. What are stored procedures and functions in PostgreSQL, and how do they differ?
- **Stored Procedures**: Can perform multiple operations but do not return a value.  
- **Functions**: Return a value and can be used in queries.

### Example of a Function:
```sql
CREATE FUNCTION get_total_sales() RETURNS NUMERIC AS $$
    SELECT SUM(amount) FROM sales;
$$ LANGUAGE SQL;
```
Call the function:
```sql
SELECT get_total_sales();
```

### Example of a Stored Procedure:
```sql
CREATE PROCEDURE update_salary(IN emp_id INT, IN new_salary NUMERIC) AS $$
BEGIN
    UPDATE employees SET salary = new_salary WHERE id = emp_id;
END;
$$ LANGUAGE plpgsql;
```
Call the procedure:
```sql
CALL update_salary(1, 50000);
```

---

Let me know if you need modifications! 🚀



