### 1. What is the difference between Runnable and Callable in Java?
In Java, both Runnable and Callable are used for defining tasks in multithreading, but they have key differences:

Runnable has a run() method that does not return a value and cannot throw checked exceptions. It is used when we just need to execute a task without a result.

Callable has a call() method that returns a result and can throw checked exceptions. It is useful when we need a computed result from a task.

Runnable is executed using Thread or ExecutorService, whereas Callable is executed only via ExecutorService, which returns a Future to retrieve the result.

### 2. What is ExecutorService in Java?
ExecutorService is a part of Java's java.util.concurrent package that provides a higher-level replacement for managing threads. 
Instead of manually creating and managing threads, we use ExecutorService to handle thread execution efficiently.

Key Features of ExecutorService:
Thread Pooling → Reuses a fixed number of threads instead of creating new ones.

Task Submission → Supports both Runnable (no return value) and Callable (returns a result).

Future Support → When using Callable, it returns a Future object to get the result asynchronously.

Graceful Shutdown → Provides shutdown() and shutdownNow() methods to stop tasks properly.

### What is CompletableFuture in Java?
CompletableFuture is a class in Java used for asynchronous programming. 
It helps run tasks in the background without blocking the main thread. 
It is part of java.util.concurrent and improves performance in multi-threaded applications.

Why use CompletableFuture?
Runs tasks in the background (runAsync() and supplyAsync()).

Chains multiple tasks (thenApply(), thenAccept(), thenRun()).

Combines multiple tasks (thenCombine(), thenCompose()).

Handles errors (exceptionally(), handle()).

