# Container

To understand Containers, we need to understand Virtualization first.

### Virtualization
Docker utilizes built-in kernel features to fully isolate resource control at the process level. Containers use these technologies to create lightweight images that act as a standalone piece of software that carries everything it needs inside the box.

There are several types of Virtualization, namely Application Virtualization, Network Virtualization and Storage Virtualization.

### Container image
Image is a snapshot of the filesystem at a given point. Containers use the idea of `copy-on-write` storage, which is able to create a brand new container immediately, without having to wait on copying out a whole new filesystem. Copy-on-write storage keeps track of what's changed.

### Key Container Concepts
* cgroups - limits how much of a thing you can use
* namespace - limits what you can see
* union filesystems - allows for efficient storage, download and execution of images. The easiest way to understand union filesystems is to think of them like a layer cake with each layer baked independently.

### Container Definition
Containers are a type of Operating System Virtualization. A collection of software processes unified by one namespace, with access to an operating system kernel that it shares with other containers and has little to no access between containers.

##### Docker's definition
A runtime instance of a Docker image, contains:
  - A Docker Image
  - An execution environment
  - A standard set of instructions

##### Definition from Object Oriented world
Container is an object, while Class is the Docker Image

##### How is Container different than Virtual Machines
A VM can have one or many applications. Has all the necessary binaries and libraries. Includes the entire guest operating system to interact with the application.

On the other hand, Container includes the application and all of its dependencies. A Container shares the kernel with the other containers. Containers are not tied to any specific infrastructure, they only need Docker engine installed on the host.
Containers run an isolated process in user space on the host operating system.

## Benefits!

##### Developers View
  - Applications are portable and packaged in a standard way.
  - Deployment is easy and repeatable
  - Testing can be automated
  - Packaging and integrations can be automated as well
  - Support newer microservices architecture
  - Alleviate platform compatibility issues

##### DevOps View
  - Reliable deployments
  - Improved speed and frequency of releases
  - Consistent application lifecycle: configure once and run multiple times
  - Consistent environments: no more process differences between dev and production
  - Simple scaling: fast deployments east the addition of workers and permit workload to grow anad shrink for on-demand use.

##### Overall
  - Containers create a common langugage between developers and devOps folks
  - Containers bring agility to code and help build a continuous integration and deployment pipeline
