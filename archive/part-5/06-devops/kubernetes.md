# Kubernetes (K8s)
Definition: Open source platform designed to automate deploying, scaling and operating application containers. 
Goal: to foster an ecosystem of components and tools that relieve the burden of running applications in public and private clouds.

```
Containers package an application so it can be easily deployed to run in its own isolated environment.
Kubernetes is a platform to schedule and run containers on clusters of virtual machines.
It runs on bare metal, virtual machines, private datacenter and public cloud.
```

### Features
  - Multi-host container scheduling
    - Done by kube-scheduler
    - Assigns pods to nodes/host at runtime
    - Accounts for resources, quality of service, policies and user specifications before scheduling
  - Scalability and Availability
    - K8s master can be deployed in a highly available configuration
    - Multi-region deployments are available
    - Architectire in v1.8 supports upto 5000 node clusters and can run 150,000 pods
    - Pods can be horizontally scaled via an API
    - Scalability features
        - Registration: New worker nodes can seamlessly register themselves with master node
        - Service discovery: Allows automatic detection of new services and endpoints via DNS or environment variables
  - Flexibility and Modularization
    - Plug-and-play architecture
    - Extend architecture when needed
    - Add-ons: Network drivers, service discovery, container runtime, visualization and command
  - Persistent Storage
    - Pods can use persistent volumes to store data
    - Data retained across pod restarts and crashes
  - Application upgrades and Application rollbacks
  - Maintenance: turn off/on host during maintenance
  - Logging and monitoring
    -  Monitoring is built-in
    -  TCP, HTTP, container execution health check
    -  Node health check with failures monitored by node controller
    -  Kubernetes status can be monitored by Heapster and cAdvisor
    -  Use existing logging frameworks like ELK
  - Secret Management
    - Mounted as data volumes or environment variables
    - Specific to namespace

### Architecture
  - Master node - responsible for overall management of Kubernetes cluster
    - API server (FE) - Communication
    - Scheduler - Scheduling
    - Cluster/Controller Manager - Controllers
  - etcd - Simple distributed key-value store, K8s uses it as its database and stores all cluster data here. Data like job scheduling info, pod details, state information, etc.
  - kubectl - command-line application to interact with Master node
    - config file: kubeconfig
        - server information
        - authentication information to access api server
  - Worker node - nodes where applications operate
    - kubelet - process that handles communication to master node. Agent that communicates with the API server.
    - Docker - run containers on the node
        - pod - containers of an application are tightly coupled in a pod. Pod is a smallest unit that can be scheduled for deployment with Kubernetes. The group of containers within pod share storage, linux namespace, IP addresses, etc
    - kube-proxy - process for network proxy and load balancer. Also handles network routing for TCP and UDP packets.

### Hardware

##### Node
Smallest unit of computing hardware in Kubernetes. It is a representation of single machine in your cluster. In most production systems, a node will likely be either a physical machine in a datacenter, or virtual machine hosted on a cloud provider like GCP. In theory, you can make a node out of almost anything.
Thinking of a machine as a “node” allows us to insert a layer of abstraction. Simply view each machine as a set of CPU and RAM resources that can be utilized. In this way, any machine can substitute any other machine in a Kubernetes cluster.

Serves as a worker machine in K8s cluster. 

###### Requirements
- A kubelet running
- Container tooling like Docker
- A kube-proxy process running
- a process like supervisord

##### Cluster
In Kubernetes, nodes pool together their resources to form a more powerful machine. When you deploy programs onto the cluster, it intelligently handles distributing work to the individual nodes for you. If any nodes are added or removed, the cluster will shift around work as necessary. It shouldn’t matter to the program, or the programmer, which individual machines are actually running the code.

Kubernetes in production recommends atleast a three-node cluster

##### Persistent Volumes
Because programs running on your cluster aren’t guaranteed to run on a specific node, data can’t be saved to any arbitrary place in the file system. If a program tries to save data to a file for later, but is then relocated onto a new node, the file will no longer be where the program expects it to be.
For this reason, the traditional local storage associated to each node is treated as a temporary cache to hold programs, but any data saved locally can not be expected to persist.

To store data permanently, Kubernetes uses Persistent Volumes. While the CPU and RAM resources of all nodes are effectively pooled and managed by the cluster, persistent file storage is not. Instead, local or cloud drives can be attached to the cluster as a Persistent Volume. This can be thought of as plugging an external hard drive in to the cluster. `Persistent Volumes provide a file system that can be mounted to the cluster, without being associated with any particular node.`

### Software

##### Containers
Programs running on Kubernetes are packaged as Linux containers. Containers are a widely accepted standard, so there are already many pre-built images that can be deployed on Kubernetes.

Containerization allows you to create self-contained Linux execution environments. Any program and all its dependencies can be bundled up into a single file and then shared on the internet. Anyone can download the container and deploy it on their infrastructure with very little setup required.

Creating a container can be done programmatically, allowing powerful CI and CD pipelines to be formed.

Multiple programs can be added into a single container, but you should limit yourself to one process per container if at all possible. It’s better to have many small containers than one large one. If each container has a tight focus, updates are easier to deploy and issues are easier to diagnose.

##### Pods
Kubernetes doesn’t run containers directly; instead it wraps one or more containers into a higher-level structure called a pod. Any containers in the same pod will share the same resources and local network. Containers can easily communicate with other containers in the same pod as though they were on the same machine while maintaining a degree of isolation from others.

Pod is a simplest unit that you can interact with. You can create, deploy and delete pods. It represents one running process on your cluster. If a pod dies for some reason, it will not be rescheduled. Always use higher-level constructs to manage and add stability to pods called controllers.

`Don't use a pod directly. Use a controller instead like a deployment.`

###### what's in here?
- Docker application container
- Storage resources
- Unique network IP
- Options that govern that how a container should run

###### States
- Pending - Pod has been accepted by the K8s system but the container has not been created yet.
- Running - Pod has been scheduled on a node and all of its containers are created and atleast one container is in a running state.
- Succeeded - All containers in a pod have exited with an exit status of 0. This indicates successful execution and will not be restarted.
- Failed - All the container in the pod have exited and atleast one container has failed and returned a non-zero exit status.
- CrashLoopBackOff - Container fails to start for some reason and K8s tries over and over and over again to start the pod.

##### Minikube
Tool to run K8s locally. A light-weight K8s implementation that creates a VM on your local machine and deploys a simple cluster containing only one node.

Minikube runs a Docker engine to be able to start containers. In order to access this Docker engine from your local machine using your local Docker client, you’ll need to set up the correct Docker environment with minikube docker-env.

##### Controllers

###### Benefits
- Application reliability - Multiple instances of an application running, prevent problem if one or more instances fail
- Scale - When pod experience high volume of requests, K8s allow us to scale up the pods
- Load balancing - Multiple versions of the pod running allow traffic to flow through different pods and doesn't overload one single pod or node.

###### Type of Controllers
- ReplicaSets - Ensures that a specified number of replicas for a pod are running at all times. If the number of pods are less that ReplicaSets expect, it'll start up a new pod.
- Deployments - provides declarative updates for pods and ReplicaSets. Internally Deployment manages ReplicaSets, which internally manages Pod. Hence deployments can automatically support rollback mechanism.
    - Use Cases
        - Pod management: Running a ReplicaSet allows us to deploy a number of pods, and check their status as a single unit.
        - Scaling a ReplicaSets scales out the pods, and allows for the deployment to handle more traffic.
- DaemonSets - Ensures that all the nodes run a copy of specific pod. As nodes are added or removed from the cluster, a DaemonSet will add or remove the required pods. Deleting the DaemonSets will cleanpup all the pods it created.
- Jobs - Supervisor process for pods carrying out batch jobs. Used to run individual processes that run once and complete successfully, example Cron job.
- Services - Provides network connectivity to one or more pods in your cluster. Allow the communication between one set of deployments with another. Each service is assigned a unique IP address that never changes through the lifetime of the service. Pods are then configured to talk to the service and then rely on the service IP for any request that might be sent to the pod. Use a service to get two pods in two deployments to talk to each other. Using a pod IP to communicate is a bad choice since they can change at anytime.
    - Internal Services - IP is only reachable only within the cluster
    - External Services - endpoint available through node ip:port (NodePort)
    - Load balancer - Exposes application to the interent


### Organizing Applications
- Labels - Used by K8s to identify attributes for objects. Key/Value pairs that are attached to objects like pods, services and deployment. Example: release, environment, tier
- Selectors - used by kubectl command to list and filter objects on labels applied.
    - Equality-based
    - Set-based
- Namespaces - used where there are many users and teams, and you want to allow teams to access resources, with accountability. Great way to divide cluster resources between users. Teams can have authentication within their own namespaces.

### kubelet and kube-proxy

##### kubelet
The Kubernetes node agent that runs on each node.
- Communicates with the API server to see if pods have been assigned to nodes
- Executes pod containers via a container engine
- Mounts and runs pod volumes and secrets
- Executes health checks to identify pod/node status and reports back to the API server
- **Important:** kubelet only manages containers that were created by the API server -- and not any container running on the node.

##### Podspec
YAML file that describes the pod.
kubelet takes a set of Podspecs that are provided by the kube-apiserver and ensures that the containers described in those Podspecs are running and healthy.

##### kube-proxy -- The Network Proxy
Watches the API server for the addition and removal of services. Then for each new service, kube-proxy opens a randomly chosen port on a local node. Any connections made to that port are proxied back in corresponding pods.
- Process that runs on all the worker nodes
- Reflects services as defined on each node, and can do simple network stream or round-robin forwarding across a set of backends.
- Service cluster IPs and ports are currently found through Docker-link compatible environment variables specifying ports opened by the service proxy

###### kube-proxy modes
- User Space mode
- Iptables mode
- Ipvs mode
