### 1. Write a program to print a string based on given conditions?  
   a) When the given number is divisible by **3**, print **tic**.  
   b) When the given number is divisible by **5**, print **toe**.  
   c) When the given number is divisible by **both 3 and 5**, print **tictoe**.  
   d) When the given number is divisible by **7 and also by 3 & 5**, print **tictoetoo**.
       **Answer:**  
```java
public class TicToe {
    public static void main(String[] args) {
        int n = 105;
        String result = "";

        if (n % 3 == 0) {
            result += "tic";
        }

        if (n % 5 == 0) {
            result += "toe";
        }

        if (n % 7 == 0) {
            result += "too";
        }

        System.out.println("RESULT: " + result);
    }
}
```

### 2. Write a program to print indices of array elements when two index sum is equal to given input?  
**Answer:**  
```java
import java.util.Arrays;

public class TwoSum {
    public static int[] getSumIndices(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] + arr[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{-1, -1};
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 4, 8, 9};
        int target = 13;
        System.out.println(Arrays.toString(getSumIndices(arr, target)));
    }
}
```
### 3. Explain security implementation in Rest API in spring boot ?
**Answer:**  </br>
In Spring Boot REST API, security is mainly implemented using Spring Security.
  * <b>Authentication:</b> It verifies users by using their credentials like username and password.
  * <b>Authorization:</b> It checks what you can access based on your role (like ADMIN, USER).
  * <b>JWT (JSON Web Token):</b> Used for stateless authentication. Once logged in, a token is given, and it is passed with each request for verification.
  * <b>Role-Based Access:</b> Different users get different access based on their roles.
  * <b>CSRF Protection:</b> Prevents unauthorized requests from other sites.
Security Configuration Using SecurityFilterChain (Java 17+)
```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .csrf(csrf -> csrf.disable()) // Disable CSRF for stateless API
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/api/public/**").permitAll() // Public API access
                .requestMatchers("/api/admin/**").hasRole("ADMIN") // Only ADMIN can access
                .requestMatchers("/api/user/**").hasAnyRole("USER", "ADMIN") // USER & ADMIN can access
                .anyRequest().authenticated() // All other requests need authentication
            )
            .httpBasic(); // Using Basic Authentication for simplicity

        return http.build();
    }
}
```
### 4. Write rest controller implementation for crud operations in spring boot ?
**Answer:**  </br>
Here is a simple CRUD (Create, Read, Update, Delete) REST Controller in Spring Boot:</br>
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/employees")
public class EmployeeController {

    @Autowired
    private EmployeeService employeeService;

    // Create Employee
    @PostMapping
    public ResponseEntity<Employee> createEmployee(@RequestBody Employee employee) {
        Employee savedEmployee = employeeService.saveEmployee(employee);
        return ResponseEntity.ok(savedEmployee);
    }

    // Get All Employees
    @GetMapping
    public ResponseEntity<List<Employee>> getAllEmployees() {
        List<Employee> employees = employeeService.getAllEmployees();
        return ResponseEntity.ok(employees);
    }

    // Get Employee By ID
    @GetMapping("/{id}")
    public ResponseEntity<Employee> getEmployeeById(@PathVariable Long id) {
        Employee employee = employeeService.getEmployeeById(id);
        return ResponseEntity.ok(employee);
    }

    // Update Employee
    @PutMapping("/{id}")
    public ResponseEntity<Employee> updateEmployee(@PathVariable Long id, @RequestBody Employee employee) {
        Employee updatedEmployee = employeeService.updateEmployee(id, employee);
        return ResponseEntity.ok(updatedEmployee);
    }

    // Delete Employee
    @DeleteMapping("/{id}")
    public ResponseEntity<String> deleteEmployee(@PathVariable Long id) {
        employeeService.deleteEmployee(id);
        return ResponseEntity.ok("Employee deleted successfully");
    }
}
```
<b>Explanation:</b></br>
* POST → To create a new employee.
* GET → To fetch all employees or a specific employee by ID.
* PUT → To update employee details.
* DELETE → To delete an employee by ID.
  
### 5. How to handle exception from Rest API in spring boot ?
**Answer:**</br>
In Spring Boot, you can handle exceptions in REST APIs using @ControllerAdvice along with @ExceptionHandler. This approach ensures that whenever an exception occurs, it will return a proper error response (like 404, 500, etc.) in JSON format.</br></br>

<b>Step 1: Create Global Exception Handler</b></br>
```java
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestControllerAdvice;

@RestControllerAdvice
public class GlobalExceptionHandler {

    // Handle Resource Not Found Exception
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleResourceNotFoundException(ResourceNotFoundException ex) {
        return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
    }

    // Handle Generic Exception
    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleGlobalException(Exception ex) {
        return new ResponseEntity<>("Something went wrong! " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```
<b>Step 2: Create Custom Exception Class</b></br>
```java
public class ResourceNotFoundException extends RuntimeException {
    public ResourceNotFoundException(String message) {
        super(message);
    }
}
```
<b> Step 3: Throw Exception From Controller</b></br>
```java
@GetMapping("/{id}")
public ResponseEntity<Employee> getEmployeeById(@PathVariable Long id) {
    Employee employee = employeeService.getEmployeeById(id);
    if (employee == null) {
        throw new ResourceNotFoundException("Employee not found with ID: " + id);
    }
    return ResponseEntity.ok(employee);
}
```
### 6. Difference between Authentication and Authorization ?
**Answer:** </br>
<b>Authentication:</b></br>
* Authentication is used to check the user is valid or not.
* It checks the user's username and password or any credentials.
* Example: Login Page →  enter your email/password → System verifies if it's valid or not. If it is valid, user will be authenticated.</br></br>

<b>Authorization:</b></br>
* Authorization is used for giving the access to the users after authentication.
* It provides access to the users based on roles(ADMIN, USER).
* Example: After login → ADMIN can access all APIs and USER can access limited APIs.</br></br>

<b>Simple Example:</b></br>
 * <b>Authentication:</b> → Checking your ID Card at the office gate.</br>
 * <b>Authorization:</b> → Deciding whether you can enter the CEO's cabin or just your department.
### 7. Professional challenges faced in earlier projects ?
* <b>Handling Tight Deadlines:</b>  Sometimes, I had tight deadlines to deliver a project/module.
* <b>Debugging Complex Issues in Production:</b>  critical bug reported in production and its root cause analysis.
* <b>Working with Legacy Code:</b>  In one of my projects, I had to work with legacy code that had minimal documentation and was built with older technology.
* <b>Managing Client Expectations:</b> In some projects, the client's requirements kept changing frequently.
### 8. What is Polymorphism? Provide a real-time example for it ?
Polymorphism allows an object of a subclass to be treated as an object of its superclass.</br>
<b>Real-time Example:</b></br>
Payment is a main class that supports multiple payment methods like Credit Card, UPI, Netbanking.</br>
<b>Code Example:</b></br>
```java
class Payment {
    void pay() {
        System.out.println("Processing Payment");
    }
}

class CreditCard extends Payment {
    @Override
    void pay() {
        System.out.println("Payment done using Credit Card");
    }
}

class UPI extends Payment {
    @Override
    void pay() {
        System.out.println("Payment done using UPI");
    }
}

public class PaymentTest {
    public static void main(String[] args) {
        Payment payment;

        payment = new CreditCard();
        payment.pay();  // Output: Payment done using Credit Card

        payment = new UPI();
        payment.pay();  // Output: Payment done using UPI
    }
}
```
### 9. What this snippet will print?
<b>Given Code:</b>
```java
class A {
    public void getA() {
        System.out.println("A");
    }

    public static void strip() {
        System.out.println("Strip A");
    }
}

class B extends A {
    public void getA() {
        System.out.println("B");
    }

    public static void strip() {
        System.out.println("Strip B");
    }
}

public class Test {
    public static void main(String[] args) {
        A a = new B();
        a.getA();
        a.strip();
    }
}
```
* Here, the code trying to create an object of B and assign it to reference A.
* BUT — class B does not extend class A (B is not a child of A).
* Java doesn't know the relationship between A and B, so it will throw a compilation error.
* Compilation Error -> Incompatible types: B cannot be converted to A
### 10. What is Functional Interface in Java ?
* A Functional Interface is an **interface that has exactly one abstract method (but can have multiple default or static methods).
* It is mainly used for functional programming using Lambda Expressions, Method References, and Streams API.
* It is annotated with @FunctionalInterface (optional but recommended).</br>
<b>Why Is It Used?</b></br>
* It is mainly used to write clean and concise code using Lambda Expressions instead of traditional Anonymous classes.
* Helps in functional programming.</br>

<b>Example of Functional Interface:</b></br>
```java
@FunctionalInterface
interface Calculator {
    int add(int a, int b);  // Only one abstract method
}
```
<b>Using lambda expression:</b></br>
```java
public class Test {
    public static void main(String[] args) {
        Calculator calc = (a, b) -> a + b;
        System.out.println(calc.add(5, 3));  // Output: 8
    }
}
```
### 11. What is default keyword?
* The default keyword in Java is used to create a method with a body in the interfaces.
* Before Java 8, interfaces could only have abstract methods (no body).
* From Java 8, you can define default methods with a body using the default keyword.
* We can use the default method directly without overriding it.
<b>Example:</b></br>
```java
interface Vehicle {
    void start();

    default void fuelType() {
        System.out.println("Petrol");
    }
}

class Car implements Vehicle {
    public void start() {
        System.out.println("Car Started");
    }
}

public class Test {
    public static void main(String[] args) {
        Car car = new Car();
        car.start();      // Output: Car Started
        car.fuelType();   // Output: Petrol
    }
}
```
<b>Explanation:</b>
* default void fuelType() → This is a default method with a body inside the interface.
* Car class didn't override fuelType(), but still inherited it.
* It helps in backward compatibility when adding new methods to an interface.
### 12. Why is Map used in Java?
* Map in Java is used to store data in key-value pairs.
* It is mainly used when you want to access data based on a unique key instead of an index (like in List).
* It is part of the Java Collections Framework and is found in java.util package.
### 13. Internal Working of HashMap in Java ?
* HashMap in Java is a part of the Collection Framework that stores data in key-value pairs.
* HashMap uses a technique called Hashing.
* Hashing converts the key into a hashcode (integer value) and creates index.
* So every key in the map having a unique index and hashcode.
* If Two Keys Have Same HashCode(Hash Collision), Java uses the linked list to handle the collision.</br>
  👉 Collision occurs when two different keys generate the same hashcode and try to store their data in the same index (bucket) in the HashMap array.</br>
  👉 Since the index is already occupied, HashMap uses LinkedList to store multiple values at the same index.
### 14. Put below Lists of employees into a single list with 
       Employee: id,name,address,experience
       List<Employee> ep1 - id,name, addreess
       List<Employee> ep2//id, experience
   ```java
public class MergeList {
    public static void main(String[] args) {
        List<Employee> ep1 = Arrays.asList(
                new Employee(101, "John", "New York"),
                new Employee(102, "Alice", "California"),
                new Employee(103, "Mike", "Texas")
        );

        List<Employee> ep2 = Arrays.asList(
                new Employee(101, 5),
                new Employee(102, 3),
                new Employee(103, 7)
        );

        // ✅ 🚀 One-Liner Merge Using Stream
        List<Employee> mergedList = ep1.stream()
                .map(e1 -> new Employee(
                        e1.id, e1.name, e1.address,
                        ep2.stream().filter(e2 -> e2.id == e1.id)
                                .findFirst()
                                .map(e2 -> e2.experience)
                                .orElse(0)
                ))
                .collect(Collectors.toList());

        // ✅ Print Result
        mergedList.forEach(System.out::println);

     //  ✅ 🚀 Loop-Merge
   for (Employee e1 : ep1) {
            Optional<Employee> matching = ep2.stream()
                    .filter(e2 -> e2.id == e1.id)
                    .findFirst();

            if (matching.isPresent()) {
                Employee e2 = matching.get();
                mergedList.add(new Employee(e1.id, e1.name, e1.address, e2.experience));
            }
        }

        // ✅ Printing the merged List
        mergedList.forEach(System.out::println);
    }
  ```
### 15. Advantages of Spring Boot ?
Spring Boot is a powerful framework that simplifies java application development.</br>
* <b>Auto-Configuration:</b> No need for manual configuration, Spring boot automatically configures the beans based on dependencies.</br>
* <b>Embedded Servers:</b> Spring Boot comes with built-in server tomcat. Don't need to configure the server externally.</br>
* <b>Microservice Ready:</b> Spring boot is perfect for building microservices via Spring cloud, Service discovery, API Gateway</br>
* <b>Production Ready Features:</b> Built-in health checks, metrics and logging with Spring Boot Actuator.</br>
* <b>Reduces Boilerplate Code:</b> Spring boot eleminates complex xml configurations.</br>
* <b>Powerful Dependecy Management:</b> Uses spring boot starters and uses build tools like maven, gradle efficiently.
  
### 16. Spring Boot Annotations ?
* <b>@SpringBootApplication:</b> This marks the main class of the spring boot application. It combines @Configuration, @EnableAutoConfiguration and @ComponentScan annotations. </br>
* <b>@Configutation:</b> The @Configuration annotation in Spring Boot is used to define beans and configuration settings for the Spring application context. It marks a class as a configuration class for defining beans.
* <b>@ComponentScan:</b> Scans and Registers beans from specified packages.</br>
* <b>@Bean:</b> Defines the spring bean inside the @Configuration classes. @Bean is commonly used for creating and configuring third-party components in Spring Boot.</br>
* <b>@Service:</b> Marks a service layer component. It includes business logics of the application.</br>
* <b> @Autowired:</b> Used for dependency injection.</br>
* <b>@Qualifier:</b>Specifies which bean to inject when multiple options exist.</br>
* <b>@RestController:</b> Marks a class as a REST API controller.

### 17. Why Hibernate When JPA Exists ?
* <b>JPA:</b> JPA (Java Persistence API) is just a specification that defines how Java objects should be mapped to database tables</br>
* <b>Hibernate:</b> Hibernate is an ORM framework that provides an actual implementation of JPA along with extra features like caching, batch processing, and custom queries.</br></br>

<b>Example: Specification vs Implementation:</b></br></br>
<b>i) JPA(Specification):</b></br>
This is pure JPA. But it won’t work alone without an implementation.
```java
import jakarta.persistence.*;

@Entity
@Table(name = "employees")
public class Employee {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String name;
    private String department;
    
    // Getters and Setters
}
```
<b>ii) Hibernate (Implementation):</b></br>
 Hibernate will handle database interactions, SQL generation, and performance optimizations.</br>
 ```java
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
spring.jpa.hibernate.ddl-auto=update
 ```
### 18. Explain @RequiredArgsConstructor vs @AllArgsConstructor vs @NoArgsConstructor ?
These three annotations belong to Lombok and are used to generate constructors in Java classes.</br>
* <b>@RequiredArgsConstructor:</b> Generates a constructor only for final and @NonNull fields in the java class. It automatically generates for constructor dependency injection.</br>
* <b>@AllArgsConstructor:</b> Generates a constructor with all fields in the java class.</br>
* <b>@NoArgsConstructor:</b> @NoArgsConstructor is a Lombok annotation that generates a no-argument constructor (default constructor) for a class. Allows creating an object without setting initial values.</br>

All these annotations are used to reduce boilerplate code in Java applications by automatically generating constructors  at compile time.

### 19. Extract the users from List<users> based on location is bangalore and age is > 35 ?
```java
public class FilterUsers {
    public static void main(String[] args) {
        List<User> users = Arrays.asList(
            new User("Alice", "Bangalore", 40),
            new User("Bob", "Chennai", 30),
            new User("Charlie", "Bangalore", 38),
            new User("David", "Hyderabad", 36),
            new User("Eve", "Bangalore", 28)
        );

        List<User> filteredUsers = users.stream()
            .filter(user -> "Bangalore".equalsIgnoreCase(user.getLocation()) && user.getAge() > 35)
            .collect(Collectors.toList());

        filteredUsers.forEach(System.out::println);
    }
}
```
### 20. Spring Boot Generic Exception Handling Using @ControllerAdvice ?
@ControllerAdvice is used to handle exceptions globally across all controllers in a Spring Boot application. Instead of writing try-catch blocks in every controller, you can define a centralized error-handling mechanism.

<b>Step 1: Create a Custom Exception</b></br>
```java
public class ResourceNotFoundException extends RuntimeException {
    public ResourceNotFoundException(String message) {
        super(message);
    }
}
```
<b>Step 2: Create a Global Exception Handler Using @ControllerAdvice</b>
```java
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

@RestControllerAdvice  // Alternative to @ControllerAdvice + @ResponseBody
public class GlobalExceptionHandler {

    // Handle Specific Exception (e.g., Resource Not Found)
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleResourceNotFound(ResourceNotFoundException ex) {
        return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
    }

    // Handle All Other Exceptions
    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleGlobalException(Exception ex) {
        return new ResponseEntity<>("Something went wrong: " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```
<b>Step 3: Throw an Exception in a Controller</b>
```java
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/users")
public class UserController {

    @GetMapping("/{id}")
    public String getUser(@PathVariable int id) {
        if (id != 1) {  // Simulating a missing user
            throw new ResourceNotFoundException("User not found with ID: " + id);
        }
        return "User Found";
    }
}
```
### 21. How to Secure a REST API Using Spring Security in Spring Boot?
Spring Security helps in securing REST APIs by handling authentication and authorization efficiently.</br>
<b>Step 1: Add Spring Security Dependency</b></br>
In pom.xml, add:</br>
```java
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
This enables Spring Security in your project.</br>

<b>Step 2: Create a Security Configuration Class</b></br>
We use SecurityFilterChain (recommended in Spring Boot 3) to define security rules.</br>
```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.http.SessionCreationPolicy;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.provisioning.InMemoryUserDetailsManager;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .csrf(csrf -> csrf.disable())  // Disable CSRF for APIs
            .authorizeHttpRequests(auth -> 
                auth.requestMatchers("/public/**").permitAll()  // Public access
                    .anyRequest().authenticated()  // Secure other endpoints
            )
            .sessionManagement(sess -> 
                sess.sessionCreationPolicy(SessionCreationPolicy.STATELESS) // No session
            )
            .httpBasic();  // Enable basic authentication
        
        return http.build();
    }

    @Bean
    public InMemoryUserDetailsManager userDetailsService() {
        UserDetails user = User.withUsername("admin")
                               .password("{noop}password") // {noop} means no password encoding
                               .roles("USER")
                               .build();
        return new InMemoryUserDetailsManager(user);
    }
}
```
<b>Step 3: Create a REST Controller</b>
```java
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api")
public class TestController {

    @GetMapping("/public/hello")
    public String publicHello() {
        return "Hello, this is a public API!";
    }

    @GetMapping("/secure/hello")
    public String secureHello() {
        return "Hello, this is a secured API!";
    }
}
```
### 23. Which cloud provider used for deploying the application ?
The most commonly used cloud providers are:</br></br>
<b>AWS (Amazon Web Services) - Most Popular</b>
* <b>Service:</b> AWS Elastic Beanstalk, EC2, ECS (Docker), Lambda (Serverless).
* <b>Database:</b> RDS (PostgreSQL, MySQL), DynamoDB.
* <b>Storage:</b> S3 for static assets.
* <b>Best For:</b> Scalable and enterprise-level applications.

<b>Microsoft Azure</b>
* <b>Service:</b> Azure App Service, Azure Kubernetes Service (AKS).
* <b>Database:</b> Azure SQL Database, CosmosDB.
* <b>Best For:</b> Enterprises using Microsoft technologies (.NET, Windows).

<b>Google Cloud Platform (GCP):</b>
* <b>Service:</b> Google Kubernetes Engine (GKE), Cloud Run, App Engine.
* <b>Database:</b> Cloud SQL, Firestore.
* <b>Best For:</b> AI/ML applications, startups using Google ecosystem.
  
<b>Oracle Cloud:</b>
* <b>Service:</b> Oracle Cloud Infrastructure (OCI)
* <b>Database:</b> Oracle Autonomous DB
* <b>Best For:</b> Applications needing Oracle database support







  










  
