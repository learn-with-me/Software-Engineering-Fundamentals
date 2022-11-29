# Load Balancing
Load balancing refers to efficiently distributing incoming network traffic across a group of backend servers, also known as server farm or server pool.

### Problem Statement
HTTP is not a connected protocol: it means that the session is totally independent from the TCP connections. Even worst, an HTTP session can be spread over a few TCP connections…

In a single application server will be aware the session information of all users, and whatever the number of client connections, they are all redirected to the unique server.

When using several application servers, then the problem occurs: when a user is sending requests to a server which is not aware of its session, the user will get back to the login page since the application server can’t access his session: he is considered as a new user.

### Potential Solutions
- Use a clustered web application server where the session are available for all the servers
- Sharing user’s session information in a database or a file system on application servers
- Use IP level information to maintain affinity between a user and a server
- Use application layer information to maintain persistance between a user and a server

#### Router/Load balancer
Load balancing refers to efficiently distributing incoming network traffic across a group of backend servers, also known as server farm or server pool.

#### Reverse Proxy
When working at layer 7 (aka Application layer), the load-balancer acts as a reverse proxy.

#### Sticky Sessions
A method used with the load balancer to achieve server-affinity by keeping user's session on the server. Here the router assigns a single server to a particular user, based on their HTTP session or IP address.
Source IP affinity is the latest method to use when you want to “stick” a user to a server. It will solve the issue as long as the user use a single IP address or he never change his IP address during the session.
