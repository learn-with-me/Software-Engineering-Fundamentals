# Reverse Proxy

A reverse proxy is a server that sits between client devices (such as web browsers) and a web server. Unlike a traditional forward proxy, which acts on behalf of clients to access resources from other servers, a reverse proxy handles requests on behalf of servers from clients. It serves as an intermediary between users and the backend servers, providing several benefits

1. Load Balancing
2. Web Acceleration
3. Security
4. SSL Termination:
5. Compression
6. Application Firewall

The reverse proxy receives the client request and determines the optimal backend server to handle the request based on factors like load balancing algorithms. The reverse proxy receives the response from the backend server, performs any necessary processing (e.g., compression, SSL termination), and then sends the response back to the client.

A common use case for reverse proxies is in front of web servers to optimize performance, enhance security, and streamline the management of backend servers. Popular reverse proxy software includes Nginx, Apache HTTP Server, and HAProxy.
