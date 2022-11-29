# Cloud Operations

Cloud provides environment rich with automation capabilities.

### Actions

1. Application Data
2. Data
3. Runtime
4. OS
5. Servers
6. Load balancers
7. File Storage
8. Networking

IaaS and PaaS manages actions 5-8, while SaaS manages all.

# AWS

### EC2

When we talk about compute resources in AWS, it all comes down to AWS Elastic Compute Cloud or EC2. EC2 instances are virtual machines that you launch in AWS cloud. They're created on-demand, or when combined with more advanced AWS services in response to conditions you define. EC2 goes with pay-as-you-go pricing model. You only pay for the time your instances are running.

##### Amazon Machine Image \(AMI\)

molds from which the new EC2 instances are built. They consist basic installation of operating systems. They may require you to have license for that OS \(Windows\). You can also create your custom images for future use \(say you wanted few softwares to be pre-installed\).

##### EC2 Instance Types

AWS allows you to choose from a number of pre-defined hardware configurations \(CPU, RAM and Network\), these are called instance types. Instance types generally fall into one of the instance type families. You can change the instance type anytime with just a restart.

* General Purpose - t2.nano, t2.micro. t2 series are the work-horses for EC2 instance types. Their CPUs are burstable, which means you get extra CPU power when you need it.
* Storage Optimized
* GPU instances
* Compute Optimized
* Memory Optimized - r3.large, x1.32.xlarge

> Regions - are geographical areas that are logically isolated from each other.

> Zones - Regions are divided into availability zones, where each zone is a physical data center that make up a region.

##### Elastic Block Store \(EBS\)

For disk storage, you can use instance-backed storage \(hard drive on a physical volume where your VM lives\) or Elastic Block Store, which is like an automatic hard drive installer, where it can be customized to whatever size you need. EBS lives independently of EC2, which is why it survives reboot. 

### Elastic Load Balancers \(ELB\)

Has high availability, fault tolerance and integrated SSL support. These also support cross zone load-balancing, basic HTTP health checking and integration with auto-scaling groups. You need to load listeners on ELB so they can listen to traffic. ELBs can listen on any port and can forward to any port. ELBs can also be internal \(private traffic\) only. ELBs are subject to security group that is attached to them.



