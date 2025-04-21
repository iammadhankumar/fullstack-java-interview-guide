# Java Technical Interview Questions

## Core Java Concepts :

### Java Basic Questions :

#### 1. What is the difference between JDK and JRE and JVM ?
The JDK (Java Development Kit) is a development platform for developing and running Java applications, including a compiler, libraries, and other tools. It's essential for writing, compiling, and testing Java programs.

The JRE (Java Runtime Environment) is a part of JDK. It is a software layer for running the Java programs. It includes everything needed to run Java applications such as the JVM (Java Virtual Machine) and libraries.

The JVM (Java Virtual Machine) is a virtual machine that executes Java programs by running bytecode instructions. It converts bytecode into native machine code, allowing the program to run on various operating systems.

#### 2. Why is Java a platform independent language ?
Java is platform-independent because it compiles Java code into bytecode. The JVM then converts this bytecode into machine-readable code and allowing Java to run on various operating systems.

#### 3. Explain java compiler ?
The Java compiler converts Java code into bytecode, and this bytecode can be executed by any device with a JVM.

#### 4. What is JIT compiler ?
The JIT (Just-In-Time) compiler is a part of the JVM that converts bytecode into machine readable code. This helps Java applications run faster in various devices.

#### 5. What exactly is System.out.println in Java ?
`System.out.println` is a method. It’s used to print text or variables to the console. <br>
-`System` is a class present in the `java.lang` package.<br>
-`out` is the static variable of PrintStream class that present in the System class.<br>
-`println` is the method present in the PrintStream class.

#### 6. What are the different access specifiers used in Java ?
<b>Public:</b> `public` modifier makes class members accessible from any other class.</br>
<b>Private:</b> `private` modifier makes class members accessible only with in the same class.</br>
<b>Protected:</b> `protected ` modifier makes class members accessible within the same package and by subclasses.</br>
<b>default(no specifier):</b> `default` or `no access specifier` makes class members accessible only within the same package.

#### 6. What is diamond problem in Java ?
The diamond problem happens when a class inherits from two classes that share a common parent class, leading confusion which will be the parent class. So java avoids this issue by not supporting multiple inheritance with classes. This is called diamond problem.

#### 7. What is a Marker interface in Java ?
A marker interface in Java is an empty interface with no methods. It is used to mark a class with a specific property or behavior.</br>
<b>Serializable:</b> `Serializable` is a marker interface that indicates an object can be serialized.</br>
<b>Cloneable:</b> `clonable` is a marker interface that indicates an object can be cloned.

### Java Memory Management :
#### 1. What is the difference between stack and heap memory ?
Stack memory stores temporary data like method calls and local variables. 
Heap memory stores objects and dynamic data such as arrays and lists.

#### 2. What is the difference between final, finally, and finalize ?
<b>final:</b> final keyword is used to declare constants, methods and class and it prevents changes to constants, method overriding and inheritance.</br>
<b>finally:</b> finally block used to execute code after a try-catch block, no matter if an exception occurs or not. </br>
<b>finalize:</b> finalize is a method called by the garbage collector before an unused objects is removed from memory.

#### 3. What is garbage collection ?
Garbage collection is the process of automatically finding and removing unused objects in memory to free up space and improve performance. In Java, garbage collection is supported by default, so we don't need to manage it manually.

#### 4. What part of memory Stack or Heap is cleaned in the garbage collection process ?
Garbage collection cleans up memory in the heap. It removes objects that are no longer being used, freeing up space.

#### 5. Why are strings immutable in Java ?
Strings in Java are immutable, which means once a string is created, its value cannot be changed. When you modify a string, such as by concatenating it with another string, a new string object is created instead of changing the original one. This immutability ensures safety and consistency. Java uses a string pool to store strings, and if a string with the same value already exists in the pool, it reuses that existing string. Allowing changes to string values could lead to unexpected behavior in the application, so immutability helps prevent these issues.

#### 6. What is String pool ?
The string pool in Java is a special area of memory where unique string values are stored. When a new string is created, Java first checks this pool to see if an same string already exists. If it does, Java reuses the existing string from the pool, which helps save memory and improve performance.

#### 7. What is difference between `==` and `equals` ?
`==` checks if two variables are the same object(i.e., the same memory address), while `equals()` checks if they are equal in value.

#### 8. How to handle memory leaks in java ?
A memory leak in Java happens when an object is no longer needed, but the application is still holding a reference to it, so the Garbage Collector can't remove it from memory.</br>

   <b>How to Prevent and Handle Memory Leaks</b></br>
  * Avoid keeping unnecessary object references.
  * Be careful with static variables.
  * Always close resources like streams or database connection.
  * We can use some tools like VisualVM (comes with JDK) and Eclipse Memory Analyzer Tool (MAT) to detect and fix memory leaks.
#### 9.  What kind of "leaks" GC can clear automatically ?
If an object is no longer used and there are no references pointing to it, the Garbage Collector can remove it automatically.</br>
GC Cleans Example:
```java
      // Example 1: Object becomes eligible for garbage collection
        String message = new String("Hello, Madhan!");
        message = null; // 'message' no longer references the object
        // At this point, the "Hello, Madhan!" string is eligible for GC

        // Example 2: Object remains in memory due to active reference
        String largeString = new String(new char[10_000_000]);
        // 'largeString' is assigned but not used further
        // However, it still holds a reference to the large object, so it's NOT eligible for GC

        // To make 'largeString' eligible for GC, we can nullify its reference
        largeString = null;
        // Now, the large object can be garbage collected
```


### Object-Oriented Programming :
#### 1. Explain OOPS Concept in Java ?
Object-Oriented Programming (OOP) in Java is a programming style that uses the classes and its objects to represent entities and ideas. Its a way of organizing code using objects. It focuses on four main concepts: encapsulation (hiding data), inheritance (sharing properties), polymorphism (using a single interface for different forms), and abstraction (simplifying complex systems).

#### 2. What are the Object Oriented Features supported by Java ?
<b>Encapsulation:</b> Encapsulation involves combining both data (variables) and methods into a single unit (class). It hides class variables from other classes and allows access through the class's methods. </br>

<b>Inheritance:</b> Inheritance allows one class to inherit fields and methods from another class. The class that inherits is called the subclass, and the class being inherited from is called the parent class. The extends keyword is used to indicate that one class is inheriting from another. </br>

<b>Polymorphism:</b>  polymorphism allows a parent class reference to access both methods and fields (members) of its subclasses. It achieves method overriding,  where both the parent and child classes have a method with the same name and parameters.</br>

   &nbsp; &nbsp; &nbsp;  <b>i) Compile-time polymorphism (method overloading):</b> Same method name with different parameters, decided during compile time.</br>
   &nbsp; &nbsp; &nbsp; <b>ii) Runtime polymorphism (method overriding):</b> Subclass method overrides parent class method, decided during runtime. </br>
   
<b>Abstraction:</b> Abstraction in Java is the concept of hiding internal implementation details and showing only essential features to the user. In Java, abstraction is achieved by creating abstract classes and interfaces.

<b>Class & Objects:</b> A class is a blueprint for creating objects, defining their characteristics and attributes. It can contain fields, methods, constructors, and interfaces. An object is an instance of a class and is used to access the members of that class.

#### 3. What is abstract class in java ?
An abstract class is a class that cannot be instantiated directly. Its members can be accessed by extending it in another class. It can have method without implentation like interface and with implementations.

#### 4. What is the purpose of an abstract class ?
The purpose of an abstract class is to provide a base class for other classes, It can define common features and methods that other class can inherit.
It can have both abstract methods and regular methods. We can override these methods in subclasses.

#### 5. What is interface in java ?
An interface in Java is a mechanism to achieve abstraction. It can contain a collection of abstract methods that must be implemented by a class using the implements keyword. 

#### 6. Why java doesn't support multiple inhertance ?
Multiple inheritance means a class inherits from two or more classes, which can lead to conflicts about which parent class's methods to use. That's why Java doesn't support multiple inheritance. Instead, Java uses interfaces, allowing a class to implement multiple interfaces without conflicts.

#### 7. What is constructor in java ?
A constructor is used to create and initialize objects. It has the same name as the class and is called automatically when an object is created.

#### 8. What is constructor overloading in java ?
Constructor overloading in Java means having multiple constructors in a class with different parameters.  It allows creating objects in different ways, depending on the arguments provided.

#### 9. What is the use of super keyword in Java ?
The `super` keyword in Java is used to refer to the parent class's methods and constructors. It allows you to access or override methods and constructors from the parent class.

#### 10. What is the difference between method overloading and method overriding ?
`Method overloading` is when multiple methods in the same class have the same name but different parameters.</br>
`Method overriding` is when a subclass provides a new implementation for a method that is already defined in its parent class.

#### 11. What is the difference between static methods, static variables, and static classes in Java ?
`Static methods` and `static variables belong` to the class itself rather than to objects. They can be accessed using class name directly without creating an instance of the class.</br>
In Java, a top-level class cannot be static. Only nested (inner) classes can be declared static, and these must be accessed through an instance of the outer class.

#### 12. Why aren't classes typically declared as static in Java ?
In Java, the keyword `static` is used to define features that belong to a class. `static` members can be accessed directly using class name without creating objects. So concept of static does not apply to top-level classes and it belongs to the class.

#### 13. What is the difference between composition and inheritance ?
`Composition ("has-a" relationship)` means that one class contains an object of another class as a member and representing has-a relationship. </br>
`inheritance ("is-a" relationship)` ` means one class is inherited from another class and representing is-a relationship.

#### 14. Difference between instance variable and local variables ?
Instance variables are declared inside a class but outside methods,and they belong to an object of the class. They can be accessed and modified by any method in the class. </br>
Local variables are declared inside a method or block are accessible only with in the block.

#### 15. Difference between constructor and method ?
A `constructor` is a special block of code that runs when an object is created. Its main purpose is to create and initialize the object. It has the same name as the class and does not have a return type. </br>
A `method` is a regular function defined in a class that performs actions or calculations, It can be called by using the object of the class and mostly it can return value except void method.

#### 16. Explain about SOLID principles in java ?
SOLID principles are used to write clean, maintainable, and scalable code. It consists five design principles.</br>
* <b>Single Responsibility Principle(S):</b> Every class should only have one responsibility. If a class handles multiple concerns, changes in one functionality might affect the other, making maintenance difficult.</br>
<b>Realtime Example:</b> A bill generator class should only generate bills, not send emails.</br>
* <b>Open/Closed Principle(O):</b> New features or behaviors should be added without changing the existing source code. This promotes safer and more maintainable code.</br>
<b>Realtime Example:</b> New payment methods can be added without modifying the existing payment code.</br>
* <b>Liskov Substitution Principle(L):</b> An object of a subclass should be able to replace its parent class object without causing any problems in the program.</br>
<b>Realtime Example:</b>An electric car class should replace a regular car class without changing expected behavior like starting, stopping, or driving.</br>
* <b>Interface Segregation Principle (I):</b>  A class should not be forced to implement methods it doesn't need.</br>
<b>Realtime Example:</b>A simple text editor class shouldn't be forced to implement image editing functions.</br>
*  <b>Dependency Inversion Principle (D):</b> Code should depend on interfaces or abstract classes, not on concrete classes. This makes the system flexible, decoupled, and easy to change.</br>
<b>Realtime Example:</b>An online store class should depend on a payment gateway interface, not on a specific payment service like PayPal or Razorpay.



### Java 8 Features :
#### 1. What are the key features introduced in Java 8 ?
Java 8 introduced several key features: </br>
Lambda Expressions, Functional Interfaces, Method References, Stream API, Optional Class, New Date-Time API, ForEach() method, default and static methods, Collectors class.

#### 2. What is Lambda Expressions ?
Lambda expression is a important feature of Java which was included in Java SE 8. It provides a clear and concise way to represent one method interface using an expression. It is very useful in collection library. It helps to iterate, filter and extract data from collection.

<b>Without Lambda:</b> </br>
```java
Runnable r = new Runnable() {</br>
    @Override</br>
    public void run() {</br>
        System.out.println("Hello, World!");</br>
    }</br>
};
```

<b>With Lambda:</b></br>
```java
Runnable r = () -> System.out.println("Hello, World!");</br>
```
The lambda () -> System.out.println("Hello, World!") simplifies the code to just one line.

#### 3. What is Functional Interfaces ?
Functional interfaces are interfaces with just one abstract method (but can have multiple default or static methods). It is used for functional programming. They enable functional programming by using lambda expressions or method references.</br>
For example, `Runnable` is a functional interface because it has only one method `run()`.

#### 4. Types of functional interfaces ?
Java provides several built-in functional interfaces under the java.util.function package.</br>
##### Function:
- **Abstract Method:** `R apply(T t)`  
- **Description:** Takes one input, returns one output
- **Example:** ```java Function<Integer, Integer> square = x -> x * x; ```
##### Predicate:
- **Abstract Method:** `R apply(T t)`  
- **Description:** Takes one input, returns true/false	
- **Example:** ```java Predicate<Integer> isEven = x -> x % 2 == 0; ```
##### Consumer:
- **Abstract Method:** `void accept(T t)`  
- **Description:** Takes one input, returns nothing (used for actions like printing)
- **Example:** ```java Consumer<String> print = System.out::println; ```
##### Supplier:
- **Abstract Method:** `T get()`  
- **Description:** Takes no input, returns a value	
- **Example:** ```java Supplier<Double> randomNumber = Math::random; ```
##### UnaryOperator:
- **Abstract Method:** `T apply(T t)`  
- **Description:** Takes one input and returns one output, but input and output are the same type
- **Example:** ```java UnaryOperator<Integer> increment = num -> num + 1; ```

#### 5. What is Method References ?
Method references are a simple way to use existing methods with lambda expressions. A method can be referred to directly by using the class name, which simplifies the code. </br> For example, `String::toLowerCase` directly uses the `toLowerCase` method of the String class.

#### 6. Explain about Stream API ?
The Stream API in Java is used to process collections of data. It allows filtering, mapping, and combining data in a simple and readable way. Streams can handle large amounts of data efficiently and support parallel processing.

#### 7. Explain about Optional class ?
Optional is a class that may or may not hold a value. It helps avoid NullPointerException by providing methods to check if a value is present. It handles null cases more safely and clearly.

* Optional.of(): Creates an Optional containing a non-null value; it throws a NullPointerException if the value is null.

* Optional.ofNullable(): Creates an Optional that can contain either a non-null value or be empty (null-safe).

#### 8. Explain about new Date-Time API ?
The new Date-Time API in Java simplifies working with dates and times. It is part of the java.time package and makes it easier to handle time zones and perform calculations.

#### 9. What is forEach method in Java ?
The forEach() method is used to iterate over elements in a collection or stream. It was introduced in Java 8 as part of the Stream API and performs an action on each item in the collection or stream.

#### 10. What default and static methods in interfaces ?
`Default methods` in interfaces provide a default implementation that can be implemented by classes.</br>
`Static method`s belong to the interface itself and can be called without creating an instance.

#### 11. What is Collectors class in the Stream API ?
The Collectors class in the Stream API helps to collect results from a stream into different forms like lists, sets and maps.

### Exception Handling :
#### 1. What is exception ?
An exception in Java is an error that disrupts the normal flow of the program. Its like problem that stops the program from working correctly.

#### 2. What is exception handling ?
Exception handling is a way to manage errors that occur during a program’s execution. In Java we can use, try catch blocks to catch and handle exceptions, allowing the program to continue running smoothly even if something goes wrong.

#### 3. What is the difference between checked and unchecked exceptions ?
Checked exceptions are errors that must be handled explicitly in the code at a compile time. Ex. IOException </br>
Unchecked exceptions are runtime errors. Ex. NullPointerException, ArrayIndexOutOfBoundsException

#### 4. What is the use of try-catch block in Java ?
The `try-catch` block is used to handle exceptions in Java. The try block contains code that might cause an error, and the catch block contains code to handle that error if it happens. This prevents the program from crashing and allows to run smoothly.

#### 5. What is the difference between throw and throws ?
`throw` is used to manually trigger an exception within a method. </br>
`throws` is used in a method declaration to specify that the method can throw certain exceptions, which need to be handled by the calling code.

#### 6. What is the use of the finally block ?
The `finally` block in Java is used to ensure that certain code runs no matter what, whether an exception occurs or not. It's typically used for cleanup activities, like closing files or releasing resources.

#### 7. What's the base class of all exception classes ?
The base class of all exception classes in Java is Throwable.

### Multithreading :

#### 1. What is a thread and what are the different stages in its lifecycle ?
A thread in Java is a small task that runs independently within a program. Threads allow multiple tasks to be performed at the same time. </br>
<b>Different stages in thread:</b>
* <b>New:</b> The Thread is created, but yet started. </br>
* <b>Runnable:</b> The thread is ready to run and waiting for the system scheduler to allocate CPU time to execute it. Runnable state occurs after start() is called.</br>
* <b>Blocked:</b> The thread is waiting for the lock that another thread is using to become available. </br>
* <b>Waiting:</b> The thread is waiting for another thread to complete its task before it can continue. </br>
* <b>Terminated:</b> The thread has completed its task or has been stopped.</br>



#### 2. What is the difference between process and thread ?
A process is an independent program with its own memory space, while a thread is a smaller execution unit within a process.

#### 3. What are the different types of thread priorities available in Java ?
In Java, threads can have three priority levels: </br>
<b>Low (MIN_PRIORITY):</b> Priority level 1.</br>
<b>Normal (NORM_PRIORITY):</b> Priority level 5, which is the default.</br>
<b>High (MAX_PRIORITY):</b> Priority level 10.</br>
Threads with higher priority run before lower-priority threads.

#### 4. What is the difference between user threads and Daemon threads ?
User threads are the main threads running tasks, while daemon threads run in the background and stop when the main program ends.

#### 5. What is synchronization ?
Synchronization ensures that only one thread can execute a at a time, It prevent issues like race conditions and data corruption when multiple threads executed at a time.

#### 6. What is race condition ?
A race condition happens when two or more threads run at the same time and try to use the same data. This can lead to unexpected behavior or errors.

#### 7. What is a deadlock ?
A deadlock occurs when two or more threads are stuck waiting for each other to complete their tasks, keeping all threads in a waiting state.

#### 8. What is the use of the wait() and notify() methods ?
`wait()` makes a thread stop and release its lock, waiting for another thread to signal it to continue. </br>
`notify()` wakes up a thread that is waiting, allowing it to resume work.

#### 9. What is the difference between synchronized and volatile in Java ?
`synchronized` allows only one thread to run a block of code at a time to avoid conflicts.</br>
`volatile` keyword in Java is used to indicate that a variable's value can be modified by different threads.

#### 10. What is the purpose of the sleep() method in Java ?
The `sleep()` method in Java pauses a thread for a specified amount of time, temporarily stopping its execution.

#### 11. What is the difference between wait() and sleep() in Java ?
`wait()` method is used to pause a thread until another thread notifies it to continue. It must be called from within a synchronized block or method.</br>
`sleep()` simply pauses a thread for a specified amount of time.

#### 12. What is the difference between notify() and notifyAll() in Java ?
`notify()` wakes up one waiting thread.
`notifyAll()` wakes up all waiting threads.

#### 13. What are the differences between Thread class and Runnable interface ?
Both used to create threads in java. </br>
<b>Thread Class:</b> This class is used to define and run a thread by extending it and overriding the run() method.</br>
<b>Runnable Interface:</b> This interface is used to define a run method by implementing it. Then use it with a Thread object to start the thread. 

#### 14. How do you start a thread ?
To start a thread, create an instance of the Thread class or a class that implements Runnable interface, then call the start() method. This tells the thread to begin executing the run() method in the background.

#### 15. What is lifecycle of a thread ?
The lifecycle of a thread includes several stages:</br>
<b>New:</b> The thread is created but not started yet.</br>
<b>Runnable:</b> The thread is ready to run and waiting for CPU time.</br>
<b>Blocked:</b> The thread is waiting for a resource to become available.</br>
<b>Waiting:</b> The thread is waiting indefinitely for another thread to perform an action.</br>
<b>Terminated:</b> The thread has completed its task or has been stopped.

#### 16. What is thread pool ?
A thread pool is a collection of reusable threads that are used to perform tasks. Instead of creating new threads every time for a simple tasks we can reuse the threads in thread pool. This improves the performance and efficiency. </br> </br>
<b>newFixedThreadPool(int s):</b> The method creates a thread pool of the fixed size s.</br>
<b>newCachedThreadPool():</b> creates a thread pool with a flexible number of threads, reusing idle threads and creating new ones as needed.</br>
<b>newSingleThreadExecutor():</b> The method creates a new thread.

#### 17. Explain the concepts of livelock and starvation ?
`Livelock` occurs when two or more threads keep responding to each other without making any progress. Proper synchronization helps to overcome livelock issues. </br>
`Starvation` happens when a thread keeps getting skipped or ignored, so it never gets a chance to run because other threads are always given priority. Proper priority strategies helps to overcome starvation issues. 

#### 18. What is the java.util.concurrent package ?
The `java.util.concurrent` package in Java offers tools to manage tasks that run in multiple threads. It includes helpful features like thread pools, locks, and other utilities to make writing multithreaded programs easier and safer.

#### 19. What is lock ?
A lock is a tool that ensures only one thread can access a resource at a time, preventing conflicts.

#### 20. What is the difference between synchronized and Lock interface ?
`synchronized` locks the whole method or block of code. This means that when one thread is using a synchronized method or block, other threads have to wait until the first thread is done. It provides less control.</br>
'Lock` locks the specific sections of the code as needed. This can help improve performance in some cases.

#### 21. What is ReentrantLock and ReentrantReadWriteLock ?
`ReentrantLock` is a class that implemented lock interface to provide syncronization, It allows the same thread to acquire the lock multiple times without getting stuck. </br>
`ReentrantReadWriteLock` is a special type of lock that allows multiple threads to read a resource at the same time but only one thread to write. 

#### 22. What is BlockingQueue ?
A `BlockingQueue` in Java is a queue where threads can wait if it’s full or empty. Threads are blocked until space becomes available for adding elements or retrieving elements in the queue.



















