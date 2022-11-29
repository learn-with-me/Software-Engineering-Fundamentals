# Microservices

The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource API. These services are built around business capabilities and independently deployable by fully automated deployment machinery. There is a bare minimum of centralized management of these services, which may be written in different programming languages and use different data storage technologies.
Variant of service-oriented architecture that structures the entire application as a collection of loosely coupled services. `- Martin Fowler`

```
1. Read more about 12 factor apps
2. Patterns
   - Building block architecture
   - Deployment patterns
   - Runtime patterns
```

### Building block architecture
##### Codebase workflow
  - Push code to source control
  - Automated build is kicked off to build and run tests against the code
  - Build container image and push to image repository

##### Application Dependencies
  - Applications modeled in kubernetes are implemented as deployments and break into pods
  - Single pod can have many containers inside
  - Common seen in Kubernetes: sidecar pattern

##### Dev vs Prod
  - small footprint: different namespaces with different credentials for dev, staging and production
  - large footprint: unique Kubernetes installation for dev, staging and production

##### Admin processes
  - Admin process containers tagged in a similar way to the running application
  - Containers run as Kubernetes job/cron job
  - Also run as a separate deployment

### Deployment Patterns
##### Application Configuration
- Application always have associated configuration to make the application work as expected
    - configMaps: for generic information (example: metadata, version)
    - Secrets: for sensitive data (example: passwords)
- Loaded into the pod via
    - Environment variables
    - Files
- Build, Release and Run
    - Tag containers at build time with explicit version
    - Don't use latest tag for production containers
- Running in Kubernetes
    - High-level constructs (like Deployments, ReplicaSets, DaemonSets) to run containers
    - Package management provided by Helm
    - Help adds revision control
- Processes and Port bindings
    - Processes
        - Keep application stateless
        - Don't rely on sticky sessions
        - Goal: Allow request to go to container or server by default
        - Statelessness in Kubernetes
            - Translated to Deplooyments and Pods
            - Deployments are backed by ReplicaSets, which are a collection of one or more pods
    - Port Bindings
        - Kubernetes pods are built from containers
        - Communicate to each other via well defined ports

### Runtime patters

##### Associating resources in Kubernetes
- Everything is treated as a service, and configurations are stored in a configMap or Secret

##### Logging
- Treat logs as streams: execution environment handles the logs
- Common to use a log router (Beats/Fluentd) to save the logs to a service (ElasticSearch/Splunk)
