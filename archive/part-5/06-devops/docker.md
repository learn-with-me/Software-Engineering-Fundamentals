# Docker

> Docker is an open-source engine \(native Linux technology\) that automates the deployment of applications into containers.
>
> Docker wants you to be able to build, ship/deploy and run distributed applications \(to avoid single point of failure\). It give you a standard way to package your software, deploy the software and run the software. What goes in the container is up to you.
>
> A container management that can consistently run software as long as a containerization system exists.

* Auto-update capability
* No additional software required such as VirtualBox

##### Competitor/Alternative to Docker

```
Rocket by CoreOS
https://coreos.com/rkt/
```

##### Workflow

```
Build    - Docker Image            // Build an application using a docker Image
Ship     - Docker Hub/Registry     // Ship an application using docker hub, Docker Trusted registry, JFrog, etc
Run      - Docker Container        // Run the application as a docker container

Docker Client (CLI)
    Stateless. Configured to talk to Docker Host.
Docker Host/Engine
    This is where the state is maintained.
    Has a Docker Daemon running, listening to incoming requests (REST API call) from the Docker CLI.
    By default configured to talk to Registry (Docker Hub).
    You can have cluster of Docker Hosts to avoid single point of failure.
Docker Registry/Hub

Docker Toolbox has Docker Engine, Docker Machine, Docker Compose and Docker Kitematic.
Ignore the toolbox, since it is needed if your Mac/Windows machine does not fulfill the basic requirements.

Free Docker Registry
--------------------
https://www.sonatype.com/docker
https://codefresh.io/docker-registry/free-private-docker-registry/
    https://codefresh.io/google-cloud/?utm_source=SumoMe&utm_medium=Banner&utm_campaign=SM2
https://canister.io/
https://treescale.com/
```

##### Steps of functionality

```
Build an image, which you'll be able to run on any operating system.
You should have a Docker Engine/Docker host running, that understands the image format.
Docker Engine takes the image format and runs the software for you.
```

##### Process

```
Dockerfile build the Docker Image, that contains all the softwares and dependencies; even Node.js.
Which means you do not need to install Node.js on your production server.

You run containers from an Image. A container consists of Web Server, Host OS, Docker Engine and Apps
```

### Core elements of Docker Ecosystem

##### Docker Engine/Host

Docker Engine is comprised of runtime and packaging tool. It must be installed on the hosts that run Docker.

```
Just like JVM understands the class format, the Docker understands the image format. It takes the image
format and runs the container for you.
This is where the containers and Images reside.
This is where we have Docker Daemon running.

Note: Docker is a native Linux technology. It is built on concepts like cgroups, namespaces, etc.
These inherently exist in Linux, so on OSX and Windows, you do have to run sort of a virtual machine.
```

##### Docker Store/Hub

Online cloud service where users can store and share their Docker images. Also known as Docker Hub.

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

##### Container

```
Each standard package is called a Docker Image..
Image for an operating system will only run on that OS. PODA is similar to WORA, but not same.
```

Using 120mb instead of 1GB

##### Building an image

```
Create a Dockerfile in an empty folder and build the image. Reason for an empty image is that entire content is sent
over from Docker client to the Docker host which is unnecessary.
You can have a .dockerignore file if you'd like to ignore few files during this transfer.
$ docker image build -t helloworld .
```

##### Resources

```
https://medium.freecodecamp.org/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b
https://www.youtube.com/watch?v=JBtWxj9l7zM
```



