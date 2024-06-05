# System Design Fundamentals

System design is a broad and complex field that encompasses many topics. Here are some fundamental topics:

### 1. **Scalability**
   - **Horizontal vs. Vertical Scaling**: Understanding the differences and when to use each.
   - **Load Balancing**: Techniques and tools to distribute traffic across servers (e.g., Round Robin, Least Connections, IP Hash).
   - **Sharding**: Dividing a database into smaller, more manageable pieces.
   - **Partitioning**: Techniques to split data across different databases or storage systems.

### 2. **Reliability**
   - **Redundancy**: Using redundant components to eliminate single points of failure.
   - **Replication**: Techniques for replicating data across multiple servers to ensure availability.
   - **Failover**: Mechanisms to switch to a standby server in case of failure.
   - **Backup and Recovery**: Strategies for backing up data and recovering from failures.

### 3. **Performance**
   - **Caching**: Implementing caches to speed up data retrieval (in-memory, distributed).
   - **Database Indexing**: Using indexes to speed up database queries.
   - **Asynchronous Processing**: Using message queues and background processing to handle long-running tasks.
   - **Content Delivery Networks (CDNs)**: Using CDNs to deliver content more quickly to users around the world.

### 4. **Data Management**
   - **Database Design**: Choosing between SQL and NoSQL, understanding normalization and denormalization.
   - **Data Consistency**: Implementing consistency models like eventual consistency, strong consistency, and CAP theorem.
   - **Data Storage**: Techniques for storing and managing data (e.g., file storage, object storage, block storage).

### 5. **Security**
   - **Authentication and Authorization**: Implementing secure access control mechanisms.
   - **Encryption**: Encrypting data at rest and in transit.
   - **Securing APIs**: Best practices for securing REST and GraphQL APIs.
   - **Network Security**: Using firewalls, VPNs, and secure network protocols.

### 6. **Distributed Systems**
   - **Microservices**: Designing applications as a collection of loosely coupled services.
   - **Service Discovery**: Mechanisms for services to find each other in a distributed system.
   - **Event-Driven Architecture**: Using events to communicate between services.
   - **Consensus Algorithms**: Implementing consensus in distributed systems (e.g., Paxos, Raft).

### 7. **Communication**
   - **HTTP/HTTPS**: Basics of web protocols.
   - **WebSockets**: Real-time communication protocols.
   - **Message Queues**: Using queues for asynchronous communication (e.g., RabbitMQ, Kafka).
   - **gRPC**: A high-performance RPC framework.

### 8. **Monitoring and Logging**
   - **Metrics**: Collecting and analyzing performance metrics.
   - **Logging**: Best practices for logging and log management.
   - **Alerting**: Setting up alerts for monitoring system health.
   - **Tracing**: Using distributed tracing to diagnose issues in microservices.

### 9. **DevOps and Automation**
   - **CI/CD Pipelines**: Implementing continuous integration and continuous deployment.
   - **Infrastructure as Code**: Managing infrastructure with code (e.g., Terraform, Ansible).
   - **Containerization**: Using containers to package applications (e.g., Docker, Kubernetes).
   - **Deployment Strategies**: Techniques for deploying updates (e.g., blue-green deployments, canary releases).

### 10. **Design Patterns**
   - **Singleton**: Ensuring a class has only one instance.
   - **Factory**: Creating objects without specifying the exact class.
   - **Observer**: Allowing objects to be notified of changes.
   - **Circuit Breaker**: Preventing calls to a failing service to allow it to recover.

### 11. **API Design**
   - **RESTful Services**: Designing REST APIs using best practices.
   - **GraphQL**: Designing APIs with GraphQL.
   - **Rate Limiting**: Protecting APIs from abuse by limiting the number of requests.

### 12. **Networking Basics**
   - **IP Addressing**: Understanding IPv4 and IPv6.
   - **DNS**: Domain Name System basics and caching.
   - **Load Balancers**: Types and strategies.

### 13. **Concurrency and Parallelism**
   - **Threads and Processes**: Understanding the difference and use cases.
   - **Synchronization**: Techniques to avoid race conditions (e.g., mutexes, semaphores).
   - **Asynchronous Programming**: Using async/await, futures, and promises.

### 14. **Storage Systems**
   - **File Systems**: Basics of file storage.
   - **Block Storage**: Used for databases and virtual machines.
   - **Object Storage**: Used for unstructured data (e.g., AWS S3).

### 15. **API Gateways**
   - **Functions**: Routing, rate limiting, security.
   - **Tools**: Implementing with tools like Kong, NGINX.

Understanding these fundamental topics will help in designing scalable, reliable, and efficient systems. Each topic has its own set of best practices, tools, and techniques, which are crucial for building robust applications.

## Additional topics to cover

* API gateway
* Consistent Hashing
* Map Reduce
* Quorum
* GeoHash, Quad Tree
* Leaky bucket, Token bucket
* federation, denormalization
* Message broker, message queue, pub-sub
* Saga pattern, event sourcing, lambda arch, kappa arch, ddd
