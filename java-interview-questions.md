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

### Object-Oriented Programming



