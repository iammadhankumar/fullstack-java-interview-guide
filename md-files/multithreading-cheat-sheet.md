### 1. Creating a Thread by Extending the Thread Class in Java :
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start(); // Starts the thread
    }
}
```
### 2. Create a Thread By Implementing the Runnable interface :
```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread is running");
    }
}

public class Main {
    public static void main(String[] args) {
        Thread thread = new Thread(new MyRunnable());
        thread.start(); // Starts the thread
    }
}
```

### Wait() and Notify() Example :
```java
package com.example.thread;

public class WaitNotifyExample {

    private static final Object lock = new Object(); // Shared lock object

    public static void main(String[] args) {
        // Define the waiting tasks by implementing Runnable
        Runnable waitingTask = new Runnable() {
            @Override
            public void run() {
                synchronized(lock) {
                    try {
                        System.out.println("Waiting first thread is waiting...");
                        lock.wait();  // Waits until notified
                        System.out.println("Waiting first thread is notified and resumed.");
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        };
        

        // Define the notifying task by implementing Runnable
        Runnable notifyingTask = new Runnable() {
            @Override
            public void run() {
                synchronized (lock) {
                    try {
                        Thread.sleep(2000);  // Simulate some work
                        System.out.println("Notifying thread is notifying...");
                        lock.notifyAll();  // Notify all waiting threads
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        };

        // Create and start threads
        Thread waitingThread = new Thread(waitingTask);
        Thread notifyingThread = new Thread(notifyingTask);

        waitingThread.start();
        notifyingThread.start();
    }
}
```
```java
### output :
Waiting first thread is waiting...
Notifying thread is notifying...
Waiting first thread is notified and resumed.
```
### 3. How do you synchronize a method or block ?
#### Synchronize a method:
```java
public synchronized void myMethod() {
    // Synchronized code
}
```
#### Synchronize a block:
```java
public void myMethod() {
    synchronized (this) {
        // Synchronized code
    }
}
```
### 4. How do you use a thread pool ?
#### Using ExecutorService:
```java
ExecutorService executor = Executors.newFixedThreadPool(10);
executor.submit(() -> {
    // Task code
});
executor.shutdown();
```
### 5. How do you set a thread as a daemon ?
A daemon thread is a background thread in Java that runs in the background and doesn't stop the program from ending when all the main tasks are done.
```java
Thread thread = new Thread(() -> {
    // Task code
});
thread.setDaemon(true);
thread.start();
```
### 6. How do you sleep a thread ?
```java
try {
    Thread.sleep(1000);  // Sleep for 1 second
} catch (InterruptedException e) {
    e.printStackTrace();
}
```
### 7. How to start a thread ?
```java
thread.start();  // Calls the thread's run() method
```
### 8. How to stop a thread ?
```java
thread.interrupt(); 
```
