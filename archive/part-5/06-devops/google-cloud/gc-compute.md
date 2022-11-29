# Compute

### Sub Domain

```
1. Compute Engine: Virtual Machines
2. App Engine: Paas for Apps and Backend. Supports Node.js, Java, Ruby, C\#, Go, Python and PHP
3. Container Engine: Run containers on GCP
4. Cloud Functions: Serverless environment to build and connect cloud services 

```

### App Engine

Allows developers to focus on writing code.

##### Flexible environment

Environment automatically scales your app up and down while balancing the load. Microservices, authorization, SQL and NoSQL databases, traffic splitting, logging, versioning, security scanning, and content delivery networks are all supported natively. Allows you to customize the runtime and even the operating system of your virtual machine using Dockerfiles.

Using it means your application instances run within Docker containers on Google Compute Engine VMs. Good candidates are applications that receive consistent traffic, experience regular traffic fluctuations, or meet the parameters for scaling up and down gradually. Also ones

* **Runtimes:** Native support for Java 8, Jetty 9, Python 2.7 and Python 3.5, NodeJS, Ruby, PHP, .NET core and Go. Developers can customize these runtimes or provide their own runtime by supplying a custom Docker image or Dockerfile from open source community.
* **Infrastructure customization:** Because VM instances in the flexible environment are Google Compute Engine virtual machines, you can take advantage of custom libraries, use SSH for debugging, and deploy your own Docker containers.
* Performance: Wide array of CPU and memory configurations. You can specify how much CPU and memory each instance of your application needs.

##### Standard environment

Based on container instances running on Google's infrastructure. Containers are pre-configured with one of the several available \(Java7, Java8, Python 2.7, Go and PHP 5.5\). Each runtime also includes libraries that support App Engine Standard APIs. For many applications, this is all you'll need. Standard environment makes it easy to build and deploy an app that run reliably under heavy load and large amounts of data.

Using it means your application runs in a sandbox, using the runtime environment of a supported language. Generally the environment is more constrained and involved, but your applications will have faster scale up times. Intended to run for free or at very low cost, since application can scale to 0 instances when there is no traffic. Another good candidate may be for applications that can experience sudden and extreme spikes of traffic that require immediate scaling.

Use Standard unless flexible is really needed

Comparison: [https://cloud.google.com/appengine/docs/the-appengine-environments](https://cloud.google.com/appengine/docs/the-appengine-environments)

### Container Engine

Container Engine is hosted and managed Kubernetes