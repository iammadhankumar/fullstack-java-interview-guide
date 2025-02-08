# Hibernate Interview Questions

#### 1. What is hibernate in spring boot ?
Hibernate is a framework in Java that simplifies database interactions by mapping Java objects to database tables. It provides several features to interact with relational databases, including: </br>
<b>ORM:</b> Maps Java objects to database tables, allowing for easy manipulation. </br>
<b>Entity Relationships:</b> Manages complex relationships between entities (e.g., one-to-many, many-to-one).</br>
<b>Transaction Management:</b> Handles transactions to ensure data consistency and integrity.

#### 2. How hibernate is it different from JDBC ?
Hibernate is an ORM framework that automates object-relational mapping and eliminates the need to write SQL queries manually, whereas JDBC requires to write explicit SQL and result handling. Hibernate also supports caching and database independence, simplifying development compared to JDBC.

#### 3. What is ORM (Object Relational Mapping) ?
ORM (Object Relational Mapping) is a technique that maps Java objects to database tables, allowing developers to interact with the database using objects instead of writing SQL. It simplifies data access and reduces boilerplate code.

#### 4. What are the core interfaces of Hibernate ?
The core interfaces of Hibernate are `Session`, `SessionFactory`, `Transaction`, and `Query`. These interfaces handle database interactions, session management, and transaction control in Hibernate.

#### 5. What is a SessionFactory in Hibernate ?
A `SessionFactory` in Hibernate is a factory class that creates Session objects for interacting with the database. It provides methods to create, read, update, and delete records in the database.  It acts as a bridge between the application and the database and responsible for creating Session objects, managing configuration, and optimizing database connections and caching.

#### 6. What is the difference between Session and SessionFactory ?
* `SessionFactory` is a thread-safe, heavyweight object responsible for configuring Hibernate, managing the connection pool, and creating Session objects.
* `Session` is a lightweight, short-lived object created from a SessionFactory that is used to interact with the database and perform CRUD operations.
  ```java
    // Create a SessionFactory (one-time setup)
    SessionFactory factory = new Configuration().configure("hibernate.cfg.xml").addAnnotatedClass(Employee.class).buildSessionFactory();
        
    // Create a session (used to interact with the database)
    Session session = factory.getCurrentSession();
  ```
  
#### 7. What is a Persistent class in Hibernate ?
A Persistent class in Hibernate is a Java class that represents a table in the database. Its objects are used to store and retrieve data from that table.

#### 8. What are the different states of an object in Hibernate ?
In Hibernate, an object can be in one of three states:</br>
* Transient (not associated with a session or database)
* Persistent (associated with a session and mapped to the database)
* Detached (was persistent but is no longer associated with a session).

#### 9. What is the purpose of the @Entity annotation ?
The `@Entity` annotation in Hibernate marks a Java class as an entity that will be mapped to a database table. It maps the class to a specific database table.

#### 10. What are the key Hibernate annotations used for mapping ?
The key Hibernate annotations used for mapping are,
* `@Entity` - maps a class to a table
* `@Id` - marks the primary key
* `@Column` - maps a field to a table column
* `@OneToMany, @ManyToOne` - for defining relationships between entities.

#### 11. What is interceptors and event listeners in hibernate ?
* Interceptors provide a way to intercept and modify the behavior of Hibernate operations, such as saving, updating, deleting, or loading entities.
* Event listeners enable you to respond to specific events that occur during the lifecycle of entities, such as before or after an entity is inserted, updated, or deleted.

