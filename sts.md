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

### 2. Do you have experience in GCP ?
I haven't worked directly with GCP, but I have strong experience in AWS (or Azure), particularly in services like EC2, S3, Lambda, and IAM. 
Since cloud platforms share many fundamental concepts, I believe I can quickly adapt to GCP.
Additionally, I have a strong foundation in cloud computing principles, and I am eager to explore GCP further.
* <b>What is Google Cloud Platform (GCP)?</b></br>
   GCP is a cloud computing platform that provides infrastructure, storage, networking, and AI/ML services.
* <b>How is GCP different from AWS and Azure?</b></br>
  GCP focuses on high-performance networking, AI/ML capabilities, and cost-effective compute options, whereas AWS is more enterprise-driven, and Azure integrates well with Microsoft products.
* <b>What are the core components of GCP?</b></br>
 The core components are Compute (VMs, Kubernetes), Storage (Cloud Storage, BigQuery), Networking (VPC, Load Balancer), Security (IAM, Cloud KMS), and AI/ML (Vertex AI, AutoML).
* <b>What are the different compute options in GCP?</b></br>
 GCP offers Compute Engine (VMs), Kubernetes Engine (GKE), Cloud Run (Serverless), and App Engine (PaaS for web apps).

### 3. Deploying Java Application on GCP ? 
You can deploy the Java application on GCP using:

* Google Compute Engine (VMs) – Deploy as a traditional server-based app.
* Google Kubernetes Engine (GKE) – Deploy as a containerized application using Docker.
* App Engine (PaaS) – Deploy a Spring Boot/Maven-based app without managing infrastructure.
  
### 4.  How to set Up GCP SDK & Authentication ?
*  Install Google Cloud SDK.
*  Create a service account with required roles (IAM -> ADMIN -> Service Account).
*  Download the JSON key file and set the env variable
