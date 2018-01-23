# Docker

> Docker is an open-source engine that automates the deployment of applications into containers.
>
> Docker wants you to be able to build, ship and run distributed applications. It give you a standard way to package your software, deploy the software and run the software. What goes in the container is up to you.
>
> A container management that can consistently run software as long as a containerization system exists.

* Auto-update capability
* No additional software required such as VirtualBox

```
Build    - Docker Image            // Build an application using a docker Image
Ship     - Docker Hub/Registry     // Ship an application using docker hub
Run      - Docker Container        // Run the application as a docker container
```

##### Process

```
Dockerfile build the Docker Image, that contains all the softwares and dependencies; even Node.js. Which means you do
not need to install Node.js on your production server.

You run containers from an Image. A container consists of Web Server, Host OS, Docker Engine and Apps
```

##### Docker Engine/Host

```
Just like JVM understands the class format, the Docker understands the image format. It takes the image format and runs
the container for you.
This is where the containers and Images reside.
This is where we have Docker Daemon running.

Note: Docker is a native Linux technology. It is built on concepts like cgroups, namespaces, etc. These inherently
exist in Linux, so on OSX and Windows, you do have to run sort of a virtual machine.
```

##### Docker Workflow

```
Docker Client
    docker build
    docker pull
    docker run
Docker Host/Engine
Docker Registry/Hub
```

##### Docker Toolbox

```
Only required, if your machine does not fulfill Docker requirements

Docker Engine
Docker Machine - A CLI. Creates a Virtualbox VM or allows to simulate Docker engine environment
                It could use VirtualBox as a virtualization provider or some other provider
Docker Compose - Allows to run multi container applications very easily
Docker Kitematic - Simple UI that allows you to manage your VMs
Virtualbox - Included for simplicity

Check Quay.io
```

##### Docker Machine

```
• Install and run Docker on Mac or Windows
• Provision and manage multiple remote Docker hosts
• Provision Swarm clusters

Tool that lets you install Docker Engine on virtual hosts, and manage the hosts with docker-machine commands.
```

Container:

Each standard package is called a Docker Image..

Image for an operating system will only run on that OS. PODA is similar to WORA, but not same.

Docker doesn't need hypervisor????

Using 120mb instead of 1GB

##### Resources

```
https://medium.freecodecamp.org/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b
https://www.youtube.com/watch?v=JBtWxj9l7zM
```



