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









  
