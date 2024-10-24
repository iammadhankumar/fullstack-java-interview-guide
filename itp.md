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
