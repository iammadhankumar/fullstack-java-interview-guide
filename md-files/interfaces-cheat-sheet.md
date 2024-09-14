## 1. Can an interface have default methods in Java ?
<b>Answer:</b> Yes 
```java
interface Car {
    void start();  // Abstract method
    
    default void stop() {  // Default method
        System.out.println("Car has stopped.");
    }
}
```
## 2. Can an interface extend multiple interfaces ?
<b>Answer:</b> Yes
```java
interface Movable {
    void move();
}

interface Flyable {
    void fly();
}

interface Vehicle extends Movable, Flyable {
    void fuelUp();
}

class Airplane implements Vehicle {
    @Override
    public void move() {
        System.out.println("Airplane is moving.");
    }

    @Override
    public void fly() {
        System.out.println("Airplane is flying.");
    }

    @Override
    public void fuelUp() {
        System.out.println("Airplane is refueling.");
    }
}
```
## 3.  Can we create an instance of an interface ?
<b>Answer:</b> No

## 4. Can an interface have private methods ?
Answer : Yes
```java 
public interface PrinterInterface {
	
 default void print() {
    setup();  // Private method usage
    System.out.println("Printing...");
}
	    
private void setup() {  // Private method
    System.out.println("Setting up the printer...");
 }
}
```
## 5. How can you achieve multiple inheritance in Java using interfaces ?
<b>Answer:</b> Java does not support multiple inheritance of classes, but it does support multiple inheritance through interfaces. A class can implement multiple interfaces, thus inheriting the abstract methods from all of them.
```java
interface A {
    void methodA();
}

interface B {
    void methodB();
}

class C implements A, B {
    @Override
    public void methodA() {
        System.out.println("Method A from Interface A");
    }

    @Override
    public void methodB() {
        System.out.println("Method B from Interface B");
    }
}

public class Main {
    public static void main(String[] args) {
        C obj = new C();
        obj.methodA();
        obj.methodB();
    }
}
```
## 6.  What will happen if a class implements two interfaces that have the same method signatures but different default implementations ?
<b>Answer:</b> If a class implements two interfaces that have the same method signature but different default implementations, the class must provide its own implementation of the method. The compiler will not know which default method to use and will throw a compilation error if the class does not provide its own implementation.
```java
interface Interface1 {
    default void show() {
        System.out.println("Interface1 show");
    }
}

interface Interface2 {
    default void show() {
        System.out.println("Interface2 show");
    }
}

class MyClass implements Interface1, Interface2 {
    @Override
    public void show() {
        System.out.println("MyClass show");
    }
}

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.show();  // Output: MyClass show
    }
}
```
## 7. Explain how you can use the @FunctionalInterface annotation.
<b>Answer:</b> The @FunctionalInterface annotation is used to indicate that the interface is intended to be a functional interface. A functional interface is an interface with exactly one abstract method, and it can have multiple default or static methods. This annotation helps to ensure that the interface conforms to this requirement.
```java
@FunctionalInterface
interface Converter {
    int convert(String s);
    
    // The following methods are allowed
    default String defaultMethod() {
        return "Default";
    }

    static void staticMethod() {
        System.out.println("Static Method");
    }
}

public class Main {
    public static void main(String[] args) {
        Converter converter = Integer::parseInt;
        System.out.println(converter.convert("123"));  // Output: 123
    }
}
```
## 8. Can you explain what happens if you try to implement an interface method in a class but the method is declared default in the interface ?
<b>Answer:</b> If a class implements a method from an interface that is declared as default, the class can either use the default implementation provided by the interface or override it with its own implementation. If the class does not override the method, the default implementation from the interface will be used.
```java
interface MyInterface {
    default void display() {
        System.out.println("Default display method");
    }
}

class MyClass implements MyInterface {
    @Override
    public void display() {
        System.out.println("Overridden display method");
    }
}

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.display();  // Output: Overridden display method
    }
}
```




