# Docker

> Docker wants you to be able to build, ship and run distributed applications. It give you a standard way to package your software, deploy the software and run the software. What goes in the container is up to you.

```
Build    - Docker Image            // Build an application using a docker Image
Ship     - Docker Hub/Registry     // Ship an application using docker hub
Run      - Docker Container        // Run the application as a docker container
```

##### Docker Engine/Host

```
Just like JVM understands the class format, the Docker understands the image format. It takes the image format and runs
the container for you.
This is where the containers and Images reside

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

Container:

Each standard package is called a Docker Image..

Image for an operating system will only run on that OS. PODA is similar to WORA, but not same.

Docker doesn't need hypervisor????

Using 120mb instead of 1GB



