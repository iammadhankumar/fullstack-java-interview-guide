### 1. How many ways we create object ?
* using new keyword
* Using Class.forName() method - This is used when you want to load the class dynamically at runtime.
* Using clone method - Creates a copy of an existing object.
  
### 2. How many ways we can create singleton class ?
Singleton class can be written as two ways.</br>
 <b>i) Eager Initialization:</b>
  Object is created at the time of class loading.</br>
  ```java
  public class EagerSingleton {
    private static final EagerSingleton instance = new EagerSingleton();

    private EagerSingleton() {
        // private constructor to prevent instantiation
    }

    public static EagerSingleton getInstance() {
        return instance;
    }
}
```
 <b>ii) Lazy Initialization:</b>
  Object is created only when requested</br>
```java
public class LazySingleton {
    private static LazySingleton instance;

    private LazySingleton() {
        // private constructor
    }

    public static synchronized LazySingleton getInstance() {
        if (instance == null) {
            instance = new LazySingleton();
        }
        return instance;
    }
}
```
### 3.  how can we maintain that singleton class to threadsafe?
To maintain a Singleton class as thread-safe, we can use two approaches.
* we can use syncronized method to return instance. This ensures that only one thread can access the method at a time, making it thread-safe. However, it may slow down performance slightly because synchronization happens every time.
* we can use double checked locking to create threadsafe singleton class efficiently. This way, synchronization only happens the first time the instance is created, and not every time the method is called.
  
### 4. What is Generics in Java?
Generics are a feature in Java that enable you to write type-safe and reusable code. They allow you to define classes, methods, and interfaces with type parameters, which can be replaced with any data type at runtime.
