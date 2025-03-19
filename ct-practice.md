### 1. Java 8 features ?
Java 8 introduced several key features:
Lambda Expressions, Functional Interfaces, Method References, Stream API, Optional Class, New Date-Time API, ForEach() method, default and static methods, Collectors class.

### 2. Lambda expressions ?
Lambda expression is a important feature of Java which was included in Java SE 8. It provides a clear and concise way to represent functional interfaces using an expression. It is very useful in collection library. It helps to iterate, filter and extract data from collection.

### 3. Functional interface ?
Functional interfaces are interfaces with just one abstract method (but can have multiple default or static methods). It is used for functional programming. They enable functional programming by using lambda expressions or method references.

Java provides several built-in functional interfaces under the java.util.function package.
```
Function:
Abstract Method: R apply(T t)
Description: Takes one input, returns one output
Example: java Function<Integer, Integer> square = x -> x * x; 

Predicate:
Abstract Method: R apply(T t)
Description: Takes one input, returns true/false
Example: java Predicate<Integer> isEven = x -> x % 2 == 0; 

Consumer:
Abstract Method: void accept(T t)
Description: Takes one input, returns nothing (used for actions like printing)
Example: java Consumer<String> print = System.out::println; 
Supplier:

Abstract Method: T get()
Description: Takes no input, returns a value
Example: java Supplier<Double> randomNumber = Math::random;
```
### 4. What is Method References ?
Method references are a simple way to use existing methods with lambda expressions. A method can be referred to directly by using the class name, which simplifies the code.
For example, String::toLowerCase directly uses the toLowerCase method of the String class.

### 5.Oops concepts ?
Object-Oriented Programming (OOP) in Java is a programming style that uses the classes and its objects to represent entities and ideas. Its a way of organizing code using objects. </br>

It focuses on four main concepts: 

* <b>encapsulation (hiding data)</b> - Encapsulation involves combining both data (variables) and methods into a single unit (class). It hides class variables from other classes and allows access through the class's methods. 
(Real-Time Example: encapsulation is a car class that hides its internal engine details and provides methods to start and stop the engine.)

* <b>Inheritance (sharing properties):</b> Inheritance allows one class to inherit fields and methods from another class. The class that inherits is called the subclass, and the class being inherited from is called the parent class. The extends keyword is used to indicate that one class is inheriting from another.
(Real-Time Example: A Manager class inheriting from an Employee class to gain attributes like name and methods like work() is another example of inheritance.)

* <b>Polymorphism (using a single interface for different forms):</b> Polymorphism allows a parent class reference to access both methods and fields (members) of its subclasses. It achieves method overriding, where both the parent and child classes have a method with the same name and parameters.
      i) Compile-time polymorphism (method overloading): Same method name with different parameters, decided during compile time.
      ii) Runtime polymorphism (method overriding): Subclass method overrides parent class method, decided during runtime.
(Real time example:A Payment class using a processPayment() method that behaves differently for CreditCard and PayPal subclasses is an example of polymorphism.)

* <b>Abstraction (simplifying complex systems):</b>  Abstraction in Java is the concept of hiding internal implementation details and showing only essential features to the user. In Java, abstraction is achieved by creating abstract classes and interfaces.
(Real time example:  Car class provides methods like drive() and brake() without exposing the internal workings of the engine.)

* <b>Class & Objects:</b>  A class is a blueprint for creating objects, defining their characteristics and attributes. It can contain fields, methods, constructors, and interfaces. An object is an instance of a class and is used to access the members of that class.

### 6. Bean Scops ?
<b>Singleton:</b> Only one instance of the bean is created for the entire Spring container. This is the default scope.</br>
<b>Prototype:</b> A new instance of the bean is created every time it is requested.</br>
<b>Request:</b> A new instance of the bean is created for each HTTP request. This scope is specific to web applications.</br>
<b>Session:</b> A new instance of the bean is created for each HTTP session. This is also specific to web applications.</br>

<b>Example:</b>
```java
    @Bean
    @Scope("singleton")
    public SingletonBean singletonBean() {
        return new SingletonBean();
    }
```

### 7. Rest API Flow ?
* <b>Define the Endpoint:</b> Decide the URL and HTTP method (GET, POST, PUT, DELETE) for the API method.
* <b>Create the Controller:</b> Write a controller class to handle the request.
* <b>Define the Method:</b>  Implement the method in the controller with appropriate annotations.
* <b>Service Layer:</b>  Create a service class to handle the business logic.
* <b>Repository Layer:</b>  If needed, interact with the database using a repository class.
* <b>Return Response:</b>  Send an appropriate response back to the client.
  
### 8. Types of exceptions ?
* <b>Checked exceptions:</b> Checked exceptions are errors that must be handled explicitly in the code at a compile time. Ex. IOException
* <b>Unchecked exceptions:</b> >Unchecked exception are runtime errors. Ex. NullPointerException, ArrayIndexOutOfBoundsException


### 9. Exception Order ?
In Java, the exception order should be from most specific to most general to ensure proper exception handling. If we use the general exception at first, it will throw the compile time error because it wont reach the specific exception.

#### 10. Caching mechanishm ?
 Caching is a technique to store frequently accessed data in memory to improve performance and reduce database load. I have used redis caching mechanisms in one of projects.
 (I used Redis to cache frequently accessed user session data, reducing database hits and improving response times.)
* <b>In-Memory Caching:</b> Stores data in the memory (RAM) for quick access. Examples include Ehcache and Caffeine.
* <b>Distributed Caching:</b> Caches data across multiple servers to ensure high availability and scalability. Examples include Redis and Memcached.
* <b>HTTP Caching:</b> Uses HTTP headers like Cache-Control and ETag to cache responses at the client or proxy level.
* <b>Database Caching:</b> Implements caching at the database level using techniques like query caching or materialized views.
* <b>Application-Level Caching:</b> Caches data within the application layer, often using frameworks like Spring Cache.

### 11. SonarQube:
Yes, SonarQube is a code quality and security analysis tool that helps identify bugs, vulnerabilities, and code smells in a project. It supports multiple languages and integrates with CI/CD pipelines to enforce coding standards. I have used it to ensure code maintainability and security by analyzing reports and fixing identified issues before deployment.

### 12. Annotations:
* <b>@Autowired:</b>  For dependency injection.
* <b>@Component, @Service, @Repository:</b>  To define Spring beans.
* <b>@Controller, @RestController:</b>  For defining controllers in Spring MVC.
* <b>@RequestMapping, @GetMapping, @PostMapping:</b>  For mapping HTTP requests to handler methods.
* <b>@Entity, @Table:</b>  For defining JPA entities.
* <b>@Transactional:</b>  For managing transactions.
* <b>@Bean:</b>  For defining beans in configuration classes.
* <b>@Value:</b>  For injecting values from properties files.

### 13. Messaging Framework
I have worked with Apache Kafka for real-time event streaming and RabbitMQ for reliable message queuing in microservices-based architectures.
(In our e-commerce application, I used Apache Kafka to stream real-time order status updates. When a customer places an order, the order service publishes an event to Kafka. The payment service consumes this event, processes the payment.)

### 14. Explain Microservices ?
Microservices is an architectural style used to break down large applications into smaller, independent services. Each service has its own codebase.

### 15. Explain about some microservices patterns ?
<b>API Gateway Pattern:</b> The API Gateway microservices pattern acts as a single entry point for all client requests. Gateway Service act as a single entry point that gets the request from client and routing them to the appropriate microservices. It handles tasks like authentication, rate limiting, and load balancing, simplifying the communication between clients and multiple backend services.</br></br>
<b>Circuit Breaker Pattern:</b>  The Circuit Breaker microservices pattern prevents a service from repeatedly trying to call a failing service. If a service is down or slow, the circuit "opens" to stop calls temporarily blocking any further requests to it. It helps prevent cascading failures by managing service failures.

### 16. Fault tolerance mechanism in java ?
Fault tolerance in Java ensures that an application continues to function even when unexpected failures occur.
Java achieves this through several mechanisms:
* <b>Try-Catch Blocks</b> – Handles exceptions gracefully without crashing the program.
* <b>Microservices Resilience</b> – Circuit Breaker patterns (e.g., Resilience4j, Hystrix) help prevent cascading failures.

### 17. How to implement fault tolerance in microservices ?
Implementing Fault Tolerance in Microservices,
* <b>Retry Mechanism:</b> Automatically retries a failed request before giving up. Example: Spring Retry, Resilience4j Retry.
* <b>Circuit Breaker Pattern:</b> Stops repeated failures from overloading a system. Example: Resilience4j CircuitBreaker, Hystrix.
* <b>Fallback Mechanism:</b> Provides an alternative response when a service is down. Example: Returning cached data or a default response.

### 18. Spring actuator ?
Spring Boot Actuator is a tool that helps monitor and manage applications in production. It provides ready-made endpoints to check the app’s health, metrics, environment, logs, and more.</br></br>
<b>Key Features:</b>
* <b>Health Check:</b> /actuator/health shows if the app is running fine.
* <b>Metrics:</b> /actuator/metrics provides CPU, memory, and request stats.
* <b>Environment Info:</b> /actuator/env shows properties and configs.
* <b>Log Management:</b> /actuator/loggers helps manage logs at runtime.</br>

It's useful for monitoring, debugging, and performance tuning in real-world applications.

### 19. How to get a constant value in spring boot from  application.properties file?
In Spring Boot, you can get a constant value from the application.properties file using @Value or @ConfigurationProperties.
```properties
# application.properties
app.name=MySpringApp
```

```java
@Value("${app.name}")
private String appName;
```
### 20. Singleton Class in java ?
A Singleton class in Java ensures that only one instance of the class exists in the JVM. It is commonly used for logging, database connections, and caching.
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {} // Private constructor

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```
### 21. How to secure Rest API Endpoint in outside URL ? 
* Use API Authentications like JWT, OAuth2.
* Enabling HTTPS to avoid external attacks.
* Restrict Access with CORS Configuration.

### 22. Remove duplicate using streams ?
```java
//String Duplications
  List<String> strings=List.of("hi","hello","hi","hello");
  List<String> uniqueStrings = strings.stream().distinct().collect(Collectors.toList());

//Character Duplication
  String input = "programming";
  String result = input.chars().distinct().mapToObj(c -> String.valueOf((char) c)).collect(Collectors.joining());
```
### 23. How to get employee list whose age is less than 30 using partitionby in java stream ?
```java
  // Partition employees based on age < 30
     Map<Boolean, List<Employee>> partitioned = employees.stream()
                .collect(Collectors.partitioningBy(emp -> emp.age < 30));

// Get employees with age < 30
    List<Employee> youngEmployees = partitioned.get(true);

    System.out.println("Employees under 30: " + youngEmployees);
```
### 24. How to get list of employees for each department ?
```java
// Group employees by department
 Map<String, List<Employee>> employeesByDept = employees.stream().collect(Collectors.groupingBy(emp -> emp.getDepartment()));
```

  







