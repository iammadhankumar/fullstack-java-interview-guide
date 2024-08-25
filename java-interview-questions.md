# Java Technical Interview Questions

## Core Java Concepts :

### Core Components of Java Execution :

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

### Java Basic Questions :
#### 1. What is the difference between stack and heap memory ?
Stack memory stores temporary data like method calls and local variables. 
Heap memory stores objects and dynamic data such as arrays and lists.

#### 2. What is the difference between final, finally, and finalize ?
<b>final:</b> final keyword is used to declare constants, methods and class and it prevents changes to constants, method overriding and inheritance.</br>
<b>finally:</b> finally block used to execute code after a try-catch block, no matter if an exception occurs or not. </br>
<b>finalize:</b> finalize is a method called by the garbage collector before an unused objects is removed from memory.

#### 3. What is garbage collection ?
Garbage collection is the process of automatically finding and removing unused objects in memory to free up space and improve performance. In Java, garbage collection is supported by default, so we don't need to manage it manually.

#### 4. What exactly is System.out.println in Java ?
`System.out.println` is a method. It’s used to print text or variables to the console. <br>
-`System` is a class present in the `java.lang` package.<br>
-`out` is the static variable of PrintStream class that present in the System class.<br>
-`println` is the method present in the PrintStream class.

#### 5. What part of memory Stack or Heap is cleaned in the garbage collection process ?
Garbage collection cleans up memory in the heap. It removes objects that are no longer being used, freeing up space.

#### 6. What are the different access specifiers used in Java ?
<b>Public:</b> `public` modifier makes class members accessible from any other class.</br>
<b>Private:</b> `private` modifier makes class members accessible only with in the same class.</br>
<b>Protected:</b> `protected ` modifier makes class members accessible within the same package and by subclasses.</br>
<b>default(no specifier):</b> `default` or `no access specifier` makes class members accessible only within the same package.

#### 6. What is diamond problem in java ?
The diamond problem happens when a class inherits from two classes that share a common parent class, leading confusion which will be the parent class. So java avoids this issue by not supporting multiple inheritance with classes. This is called diamond problem.

#### 7. What is a Marker interface in Java ?
A marker interface in Java is an empty interface with no methods. It is used to mark a class with a specific property or behavior.</br>
<b>Serializable:</b> `Serializable` is a marker interface that indicates an object can be serialized.</br>
<b>Cloneable:</b> `clonable` is a marker interface that indicates an object can be cloned.

### Object-Oriented Programming
#### 1. What are the Object Oriented Features supported by Java ?
<b>Encapsulation:</b> Encapsulation involves combining both data (variables) and methods into a single unit (class). It hides class variables from other classes and allows access through the class's methods. </br>

<b>Inheritance:</b> Inheritance allows one class to inherit fields and methods from another class. The class that inherits is called the subclass, and the class being inherited from is called the parent class. The extends keyword is used to indicate that one class is inheriting from another. </br>

<b>Polymorphism:</b>  polymorphism allows a parent class reference to access both methods and fields (members) of its subclasses. It achieves method overriding,  where both the parent and child classes have a method with the same name and parameters.</br>

   &nbsp; &nbsp; &nbsp;  <b>i) Compile-time polymorphism (method overloading):</b> Same method name with different parameters, decided during compile time.</br>
   &nbsp; &nbsp; &nbsp; <b>ii) Runtime polymorphism (method overriding):</b> Subclass method overrides parent class method, decided during runtime. </br>
   
<b>Abstraction:</b> Abstraction in Java is the concept of hiding internal implementation details and showing only essential features to the user. In Java, abstraction is achieved by creating abstract classes and interfaces.

<b>Class & Objects:</b> A class is a blueprint for creating objects, defining their characteristics and attributes. It can contain fields, methods, constructors, and interfaces. An object is an instance of a class and is used to access the members of that class.

#### 2. What is abstract class in java ?
An abstract class is a class that cannot be instantiated directly. Its members can be accessed by extending it in another class. It can have method without implentation like interface and with implementations.

#### 3. What is the purpose of an abstract class ?
The purpose of an abstract class is to provide a base class for other classes, It can define common features and methods that other class can inherit.
It can have both abstract methods and regular methods. We can override these methods in subclasses.

#### 4. What is interface in java ?
An interface in Java is a mechanism to achieve abstraction. It can contain a collection of abstract methods that must be implemented by a class using the implements keyword. 

#### 5. Why java doesn't support multiple inhertance ?
Multiple inheritance means a class inherits from two or more classes, which can lead to conflicts about which parent class's methods to use. That's why Java doesn't support multiple inheritance. Instead, Java uses interfaces, allowing a class to implement multiple interfaces without conflicts.

#### 6. What is constructor in java ?
A constructor is used to create and initialize objects. It has the same name as the class and is called automatically when an object is created.

#### 6. What is constructor overloading in java ?
Constructor overloading in Java means having multiple constructors in a class with different parameters.  It allows creating objects in different ways, depending on the arguments provided.

#### 7. What is the use of super keyword in Java ?
The `super` keyword in Java is used to refer to the parent class's methods and constructors. It allows you to access or override methods and constructors from the parent class.

#### 8. What is the difference between method overloading and method overriding ?
`Method overloading` is when multiple methods in the same class have the same name but different parameters.</br>
`Method overriding` is when a subclass provides a new implementation for a method that is already defined in its parent class.

#### 9. What is the difference between static methods, static variables, and static classes in Java ?
`Static methods` and `static variables belong` to the class itself rather than to objects. They can be accessed using class name directly without creating an instance of the class.</br>
In Java, a top-level class cannot be static. Only nested (inner) classes can be declared static, and these must be accessed through an instance of the outer class.

#### 10. Why aren't classes typically declared as static in Java ?
In Java, the keyword `static` is used to define features that belong to a class. `static` members can be accessed directly using class name without creating objects. So concept of static does not apply to top-level classes and it belongs to the class.

#### 11. What is the difference between composition and inheritance ?
`Composition ("has-a" relationship)` means that one class contains an object of another class as a member and representing has-a relationship. </br>
`inheritance ("is-a" relationship)` ` means one class is inherited from another class and representing is-a relationship.

#### 12. Difference between instance variable and local variables ?
Instance variables are declared inside a class but outside methods,and they belong to an object of the class. They can be accessed and modified by any method in the class. </br>
Local variables are declared inside a method or block are accessible only with in the block.

#### 13. Difference between constructor and method ?
A `constructor` is a special block of code that runs when an object is created. Its main purpose is to create and initialize the object. It has the same name as the class and does not have a return type. </br>
A `method` is a regular function defined in a class that performs actions or calculations, It can be called by using the object of the class and mostly it can return value except void method.



