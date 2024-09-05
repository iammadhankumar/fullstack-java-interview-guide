## Creating a Thread by Extending the Thread Class in Java :
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
## Create a Thread By Implementing the Runnable interface :
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

## Wait() and Notify() Example :
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


