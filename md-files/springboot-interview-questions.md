# Spring Boot Interview Questions

#### 1. What is springboot ?
Spring Boot is a framework that simplifies building Java applications. It provides a platform for building stand-alone and production-ready application with minimal setup. Spring Boot automatically configures the application based on the added dependencies, reducing the need to write extensive configuration code.</br> </br>
<b>Key Features of Spring Boot :</b> </br>
Auto-configuration, Embedded servers, Starter dependencies.

#### 2. Explain the benefits of spring boot ?
<b>Quick Setup:</b> Spring Boot simplifies setting up and running Java applications with minimal configuration</br>
<b>Easy Deployment:</b> Spring Boot applications can be packaged as self-contained JAR files, making deployment easy.</br>
<b>Easy Dependency Management:</b> It includes common libraries together, so managing dependencies is easier.</br>
<b>Microservices:</b> Its great for building microservices.

#### 3. Explain the features of spring boot ?
<b>Auto Configuration:</b> Spring Boot automatically configures the application based on the dependencies added, reducing the need for manual configuration.</br>
<b>Embedded Servers:</b> It includes built-in servers like tomcat, there is no need to use external servers to run the application. </br>
<b>Starter Dependencies:</b> Spring Boot provides starter dependencies that bundle common libraries and configurations for various functionalities.</br>
<b>Production-ready features:</b> Spring Boot includes features like Actuator for monitoring and managing the application, and Spring Security for securing the application.

#### 4. What is spring initializer ?
Spring Initializr is a web tool that quickly creates a new Spring boot project. It allows to select project settings, dependencies, and packaging, then generates the basic structure of the project for download.

#### 5. What is Spring Boot CLI ?
Spring Boot CLI is a command-line tool that is used for creating and running the spring boot applications.  It simplifies the process of setting up and managing the Spring Boot applications from command line interface. </br></br>
<b>To create a spring boot application:</b> `spring init --dependencies=web,data-jpa myproject`</br>
<b>To run the spring boot application:</b> for maven `./mvnw spring-boot:run` and for gradle `./gradlew bootRun`

#### 6. Give me list of build tool are there in spring boot ?
<b>Maven and Gradle:</b> Both Maven and Gradle is used for managing the depedencies and building the projects.

#### 7. What are the difference between maven and gradle ?
<b>Maven:</b> Uses XML files to define project structure and dependencies. </br>
<b>Gradle:</b> Uses Groovy or Kotlin scripts, making it more flexible and customizable. 

#### 8. Which is the default server in spring boot ?
The default server in Spring Boot is Tomcat. It comes with Spring Boot itself, so we don’t need to install it manually. Tomcat is used for running web applications, handling web requests.

#### 9. What is tomcat server and explain its internal work ?
Tomcat is a web server that runs Java applications. It processes web requests and serves web pages to users. Tomcat is a bridge between web applications and users.
It takes requests from users, runs the application code, and then sends back the appropriate web pages.

#### 10. Can Spring Boot run without Tomcat ?
The default server being used in spring boot applications is Apache Tomcat, you can use any other server of your choice like Jetty, Undertow, etc.

#### 11. How to use other servers in spring boot without tomcat ?
To use other servers in Spring Boot instead of Tomcat, </br>
i) Exclude the tomcat dependency in pom.xml using exclusions tag. (maven or gradle)</br>
ii) Include the dependency for the server we want to add.</br>
iii) Set up any necessary configurations for the new server, if required.

#### 12. Is it mandatory to add tomcat server dependency in pom.xml ?
No, it’s not mandatory to add Tomcat server dependency in pom.xml. Spring Boot includes Tomcat by default, but if you want to use a different server, you can exclude Tomcat and add the dependency for the server you prefer.

#### 13. What are the key dependencies of spring boot ?
The key dependencies of Spring Boot are:</br>
* <b>Spring Boot Starter Web:</b> For building web applications with RESTful APIs.</br>
* <b>Spring Boot Starter Data JPA:</b> For working with databases using JPA (Java Persistence API).</br>
* <b>Spring Boot Starter Security:</b> For adding security features to the application.</br>
* <b>Spring Boot Starter Test:</b> For testing the application.

#### 14. Explain about spring boot starter dependency ?
Spring Boot starter dependencies are pre-packaged sets of libraries and configurations to set up common features in the spring boot application. </br>
For example, </br>
if we add the Spring Boot Starter Web dependency, it includes everything we need to build web applications.</br>
if we add the Spring Boot Starter actuater dependency, it includes tools that monitoring and managing the application.

#### 15. How to create Spring MVC application ?
i) Firstly, Need to create spring application by including `spring-webmvc` dependency using spring initializer.</br>
ii) Configuring Spring MVC by adding the `@EnableWebMvc` annotation in the configuration class.</br>
iii) Finally Need to create necessary models, views and controller as needed.

#### 16. Explain Spring MVC architecture ?
Spring MVC is a frameword that is used for building web applications. </br>
It has three components - Model, View, Controller.</br>
<b>Model</b> - Represents the business logic of the application.</br>
<b>View</b> - Represents the frontend and Showing the data to the user as web pages.</br>
<b>Controller</b> - Handles user requests, interacts with the model, and returns the appropriate view.

#### 17. What is the difference between Controller and RestController ?
<b>Controller:</b> Handles web requests and returns web pages. It's used for traditional web applications.</br>
<b>RestController:</b> Handles web requests and returns data directly (like JSON or XML) instead of views. It’s used for building RESTful web services and APIs.

#### 18. Explain some commonly used annotations in spring boot ?
* <b>@SpringBootApplication:</b> Marks the main class of a Spring Boot application and enables auto-configuration.</br>
* <b>@RestController:</b> Used for building RESTful web services. It returns data directly (like JSON) instead of views.</br>
* <b>@RequestMapping:</b> Maps web requests to specific methods in the controller.</br>
* <b>@GetMapping:</b> A shortcut for handling GET requests.</br>
* <b>@PostMapping:</b> A shortcut for handling POST requests.</br>
* <b>@Autowired:</b> Automatically injects dependencies into your class.</br>
* <b>@Service:</b> Indicates a class provides business logic and is managed by Spring.

#### 19. Explain about @Configuration annotation ?
The `@Configuration` annotation in Spring indicates that a class provides bean definitions for the application, which are managed by the Spring IoC container. It is used to set up configurations in a Java class.

#### 20. Explain about @Bean annotation ?
The `@Bean` annotation is used to indicate that a method produces a bean to be managed by the Spring container. The `@Bean` annotation is typically used within `@Configuration` classes to define and configure beans. Mainly it is used to do custom configurations, integrating third party libraries and dependency injection.

#### 21. Explain about @ComponentScan annotation ?
 The `@ComponentScan` annotation is used for searching and registering classes as beans based on their package.  It searches for classes annotated with @Component, @Repository, @Service, and @Controller.

#### 22. Explain about Spring security ?
Spring Security is a framework which provides various security features like authentication, authorization to create secure Java Enterprise Applications.</br> Authentication verifies user identity, it supports various authentication mechanisms such as basic authentication, Oauth.</br>
Authorizations gives the access to resources after successful authentication. ex. RBAC.

#### 23. Explain the authentication and authorization ?
`Authentication` in Spring Boot involves verifying a user's identity using credentials like a username and password. This is typically achieved using mechanisms like Basic Authentication, OAuth2, or JWT (JSON Web Tokens).</br>
`Authorization` is the process of determining whether an authenticated user has the necessary permissions to access a resource or perform an action. This process is called role-based authorization.

#### 24. Tell me about Role-based Access control ?
Role-Based Access Control (RBAC) is a way to manage permissions in an application. Instead of giving permissions to each user individually, users are assigned to roles, and each role has specific permissions. For example, an `Admin` role might have access to everything, while a `User` role might only access certain features.

#### 25. What is hibernate in spring boot ?
Hibernate is a framework in Java that simplifies database interactions by mapping Java objects to database tables. It provides several features to interact with relational databases, including: </br>
<b>ORM:</b> Maps Java objects to database tables, allowing for easy manipulation. </br>
<b>Entity Relationships:</b> Manages complex relationships between entities (e.g., one-to-many, many-to-one).</br>
<b>Transaction Management:</b> Handles transactions to ensure data consistency and integrity.

#### 26. What is JPA ?
JPA (Java Persistant API) is specification that provides set of rules and interfaces for managing relational database in Java applications. It supports entity manager, TypedQuery, Creteria query for mapping the java objects into database tables.

#### 27. What is @Transactional annotation ?
The `@Transactional' annotation ensures that a series of queries are completed together successfully or none at all. It helps keep data consistent by rolling back changes if an error happens.

#### 28. What is microservices ?
Microservices is an architectural style used to break down large applications into smaller, independent services. Each service has its own codebase.

#### 29. What are the components of microservices ?
<b>Services:</b> small and independent services that has to do jobs.</br>
<b>API Gateway:</b> Handles the client request and distributes to the right services.</br>
<b>Service Registry:</b> It stores the information about the services that is running or not.

#### 30. How micro services are communicating with each other and explain it ?
Microservices communicate with each other using several methods like RestAPI, Message queues, gRPC.

#### 31. Explain about the API gateway in microservices ?
An API gateway is a server that acts as a bridge between clients and microservices. Instead of clients communicating directly with each microservice, they send requests to the API gateway. The gateway then routes these requests to the appropriate microservice and returns the response to the client. It helps manage communication, load balancing, and security.

#### 32. How to write junit testcases in spring boot ?
 To write a JUnit test case, annotate a method with @Test, and inside that method, define the test logic. Use assertions like assertEquals() or assertNull() to check expected outcomes. Ensure the test class is annotated with @RunWith or extend a specific runner if needed.




