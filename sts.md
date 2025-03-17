### 1. What are the features of java 17 ?
#### <b>Sealed Classes:</b> </br>
Sealed classes in Java (introduced in Java 15 and finalized in Java 17) restrict which classes can inherit from them. 
The permits keyword specifies the allowed subclasses. This ensures better code organization, security, and maintainability by preventing unwanted extensions.</br>

  <b>Uses:</b>
* <b>Ensuring Security:</b> Prevents unauthorized subclasses that could modify behavior.
* <b>Better Maintainability:</b> Limits extension to known classes, making code easier to manage.
* <b>Clearer Design:</b> Defines a strict hierarchy, avoiding unintended modifications.
* <b>Improved Performance:</b> Helps compilers optimize code by knowing the exact class hierarchy.
  
#### <b>Pattern Matching for Switch:</b> </br>
Pattern Matching for switch (introduced in Java 17 as a preview and finalized in Java 21) allows matching values based on their type, making switch statements more readable and type-safe.</br>
It eliminates the need for explicit casting and instanceof checks.

```java
static String typeCheck(Object obj) {
    return switch (obj) {
        case String s -> "String: " + s;
        case Integer i -> "Integer: " + i;
        default -> "Unknown type";
    };
}
```
#### <b>New RandomGenerator API:</b>
The New RandomGenerator API (introduced in Java 17) provides a more flexible and powerful way to generate random numbers.
It includes multiple implementations like L128X128MixRandom, L64X128MixRandom, and SplittableRandom, offering better performance and predictability.

```java
RandomGenerator random = RandomGenerator.of("L128X128MixRandom");
int num = random.nextInt(100);  
System.out.println(num);
```
Apart from this, Java 17 improves performance and security with better Garbage Collection (ZGC & G1), stricter encapsulation of JDK internals, native Apple Silicon support
and the deprecation of outdated features like SecurityManager and RMI Activation. 🚀
