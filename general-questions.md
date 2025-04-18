### 1. Could you please explain the Software Development Life Cycle (SDLC) that your current office follows ?

At my current office, we follow an Agile-based SDLC. Let me explain you quickly.</br>
* <b>step 1: Requirements Gathering:</b> We collaborate with stakeholders to define requirements in user stories.</br>
* <b>step 2: Planning:</b>  We conduct sprint planning to prioritize tasks and set clear deliverables and prepare sprint plab clearly.</br>
* <b>step 3: Design & Development:</b> The backend and frontend developers should be assigned, and they will receive the requirements and participate in story 
     grooming sessions before starting their work. After getting proper KT, they will start their work and complete the sprint tasks.</br>
* <b>step 4: Testing:</b> Developers will perform a one-time manual unit test before releasing it to the testing team. If everything is fine, they will hand it 
    over to the testing team, who will test it and provide feedback on the user stories. The developers will then fix the issues.</br>
* <b>step 5: Deployment:</b> We use CI/CD pipelines for smooth, automated deployments.</br>
* <b>step 6: Review:</b> after each sprint we conduct a meeting to enhance the process.</br>

### 2. Have you had experience with server administration or management?
As a software engineer, my primary focus has been on building and optimizing applications using Java, Spring Boot, and Angular. While I haven't been deeply involved in server administration, I have a solid understanding of key concepts like deployment, load balancing, and monitoring from a backend developer's perspective. I often collaborate with DevOps teams to ensure smooth deployments and address any server-related issues.

### 3. What types of servers have you had experience working with ?
I’ve primarily worked with Apache Tomcat and Nginx for deploying Java Spring Boot applications.  Additionally, I have experience deploying applications on AWS EC2 instances and managing cloud-based servers. While I focus on backend development, I collaborate with DevOps teams to ensure smooth server setups and deployments.

### 4. Could you please describe the deployment process in Tomcat ?
* <b>Build the Application:</b> Package the Java app as a WAR file using Maven.
* <b>Access Tomcat Server:</b> Connect to the Tomcat server, locally.
* <b>Deploy the WAR File:</b> Copy the WAR file into the webapps directory or use Tomcat Manager.
* <b>Start/Restart Server:</b> Tomcat extracts and runs the app; restart if needed to apply changes.
* <b>Monitor Logs:</b> Check Tomcat logs (catalina.out) to verify deployment and troubleshoot issues.

### 5. Could you please explain the concepts of Docker, Nginx, and Jenkins?
* Docker is a tool used for Containerization and it Packages applications and dependencies into lightweight containers for consistency across environments.
* Nginx is a web server used to serve static content efficiently from server and act as a load balancer and gives high performance.
* Jenkins is a CI/CD Tool that Automates building, testing, and deployment of applications using pipelines and plugins.

### 6. Tell me about database leaks and how you fix that ?
Database leaks refer to situations where sensitive data is unintentionally exposed or made accessible to unauthorized users, often due to misconfigurations or vulnerabilities in applications. </br>
To prevent this 
* <b>Restrict Access:</b> Implement role-based access controls.
* <b>Audit Regularly:</b> Perform security audits to find vulnerabilities.
* <b>Encrypt Data:</b> Use encryption for data at rest and in transit.
* <b>Use Secure Queries:</b> Employ parameterized queries to avoid SQL injection.
* <b>Monitor Access:</b> Log and review access to detect any unauthorized attempts.

### 7. how to improve the performance of the application ?
* <b>Optimize Database Queries:</b> Use indexing and avoid unnecessary data fetching.
* <b>Caching:</b> Implement caching (e.g., Redis or in-memory caching) to store frequently accessed data.
* <b>Asynchronous Processing:</b> Use background tasks for long-running processes to improve response times.
* <b>Code Optimization:</b> Refactor code to eliminate bottlenecks and improve efficiency.
* <b>Load Balancing:</b> Distribute traffic across multiple servers to prevent overload.
* <b>Minimize Resource Usage:</b> Reduce the size of assets (images, CSS, JS) and use compression.
* <b>Monitoring and Profiling:</b> Continuously monitor application performance and profile code to identify slow areas.

### 8. What are all the design patterns you have used ?
* <b>Singleton:</b> Ensures a class has only one instance and provides a global point of access.
* <b>Factory Method:</b> Defines an interface for creating objects but lets subclasses alter the type of created objects.
* <b>Observer:</b> Allows an object to notify other objects about changes in its state, promoting loose coupling.
* <b>Strategy:</b> Enables selecting an algorithm's behavior at runtime, allowing for dynamic changes.
* <b>Decorator:</b> Adds new functionality to an object dynamically without altering its structure.
* <b>Builder:</b> Facilitates constructing complex objects step by step, improving code readability and maintainability.

### 9. What are the microservices pattern you have used ?
In my experience, I’ve worked with the API Gateway pattern, which provides a single entry point for all client requests and routes them to the appropriate services. This enhances security, scalability, and simplifies client interactions.

I’ve also used the Circuit Breaker pattern to prevent cascading failures by stopping calls to a failing service, ensuring system stability and reliability.

These patterns have been essential in building resilient and scalable microservices architectures.

### 10. Do you have completed any courses ?
I’ve taken several courses through platforms like Udemy, including AWS-focused courses, to deepen my understanding of cloud services. While I haven’t pursued official certifications yet, I’m always learning to stay up-to-date with the latest skills.

### 11. What is the spring boot code structure you are following in current office ?
In my current office, we follow a modular, layered structure for Spring Boot applications to keep the code organized and maintainable:

Controller Layer: Handles incoming HTTP requests, typically located in a controller or web package. Each controller maps to endpoints for specific business functionalities.

Service Layer: Contains business logic and is usually placed in a service package. This layer processes data received from the controller before passing it to the repository.

Repository Layer: Interfaces with the database, often using JPA or Hibernate. The repository interfaces are in a repository or dao package, ensuring separation of data access from business logic.

Model/Entity Layer: Defines data structures, typically in an entity or model package. This layer includes classes mapped to database tables.

DTOs (Data Transfer Objects): Used to transfer data between layers without exposing internal structures, found in a dto package.

Configuration: Contains configuration classes for setting up security, CORS, or application properties, typically placed in a config package.

### 12. How do you call a databases ?
In our Spring Boot application, database calls start in the controller, which delegates the request to the service layer. The service then interacts with the repository layer, where Spring Data JPA manages the database operations through predefined methods. Finally, the repository translates these calls into SQL queries to interact with the database.

### 13. How do you secure your credentials ?
We keep the database name and password safe by using environment variables and special configuration files. We also use tools like Spring Cloud Config and Vault to manage sensitive information securely without putting it directly in the code.

### 14. How to you debug the particular service in microservices ?
In a microservices environment, debugging a specific service requires a structured approach. First, I check logs using centralized tools like ELK or Splunk to identify errors. If needed, I enable debug mode and attach a debugger to step through the code execution. I also use distributed tracing tools like Jaeger to track how requests flow between services. Monitoring metrics through Prometheus and Grafana helps identify performance issues. Additionally, I test API requests using Postman and verify dependencies like databases or external APIs. This systematic approach helps quickly identify and resolve issues.

### 15. how to improve performance in specific service in microservices ?

To improve the performance of a specific microservice, follow these steps:</br></br>
<b>Optimize Code & Queries:</b> Improve database queries, caching, and reduce unnecessary computations.</br>
<b>Use Caching:</b>  Implement Redis or Memcached to reduce load on databases.</br>
<b>Optimize API Calls:</b> Use pagination, batch processing, and async calls where needed.</br>
<b>Increase Scaling:</b> Use auto-scaling and load balancing to handle high traffic.</br>
<b>Optimize Resource Utilization:</b> Tune JVM, thread pools, and database connections.</br>
<b>Enable Compression:</b> Use GZIP or Brotli for faster data transfer.</br>
<b>Monitor & Tune:</b>  Use tools like Prometheus, Grafana, and APM tools (New Relic, Datadog) to analyze and optimize performance.</br>
