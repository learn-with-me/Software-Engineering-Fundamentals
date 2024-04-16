# Load Balancer

A Load balancer distributes incoming network traffic across multiple servers. Its primary purpose is to enhance the availability and reliability of applications, ensuring that no single server becomes overwhelmed with too much traffic.

It's key functions include:

1. Distribution of Traffic
2. Improving Scalability
3. Enhancing Redundancy
4. Session Persistence
5. Health Monitoring
6. Security

Load balancers can be implemented at various layers of the OSI model, including application layer (Layer 7), transport layer (Layer 4), or network layer (Layer 3), depending on the specific requirements of the application or network architecture.

In summary, load balancers play a crucial role in optimizing resource utilization, improving system reliability, and ensuring high availability for applications and services by distributing incoming traffic across multiple servers.

## Layer 4 (Transport Layer) LB

A TCP load balancer. Distributes traffic based on TCP protocol information (IP address and port).
Example: HAProxy, which balances TCP traffic.

## Layer 7 (Application Layer) LB

An HTTP load balancer. Makes decisions based on content of the HTTP header, such as URL or cookie information.
Example: NGINX, which can balance HTTP/HTTPS traffic.

## Layer 4-7 Combined LB

An Application Delivery Controller (ADC). Balances traffic based on both network and application layer information.
Example: F5 BIG-IP, offering advanced features like SSL termination and content switching.
