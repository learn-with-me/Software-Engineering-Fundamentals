# Configuraing the Cluster

> Currently, in a well-configured environment, it is recommended to not have more than 14,000 partition replicas per broker and 1 million replicas per cluster.

## Number of Brokers

The size of the cluster will be bound on the following key areas:

- Disk capacity
- Replica capacity per broker
- CPU capacity
- Network capacity

### Disk capacity

Consider how much disk capacity is required for retaining messages and how much storage is available on a single broker. If the cluster is required to retain 10 TB of data and a single broker can store 2 TB, then the minimum cluster size is 5 brokers.

### Replica capacity per broker

Increasing the replication factor will increase the storage requirements by x factor.

### CPU capacity

Consider the capacity of the cluster to handle requests. CPU usually is not a major bottleneck for most use cases, but it can be if there is an excessive amount of `client connections` and `requests` on a broker.

Keep an eye on overall CPU based on total `unique clients` and `consumer groups`.

### Network capacity

It is important to keep in mind the capacity of the network interfaces and whether they can handle the client traffic if there are multiple consumers of the data or if the traffic is not consistent over the retention period of the data.

If the network interface on a single broker is used to 80% capacity at peak, and there are two consumers of that data, the consumers will not be able to keep up with peak traffic unless there are two brokers.

If replication is being used in the cluster, this is an additional consumer of the data that must be taken into account.

You may also want to scale out to more brokers in a cluster in order to handle performance concerns caused by lesser disk throughput or system memory available.

## Broker Configuration

Requirements in the broker configuration to allow multiple Kafka brokers to join a single cluster:

1. all brokers must have the same configuration for the `zookeeper.connect` parameter
2. all brokers in the cluster must have a unique value for the `broker.id` parameter

## OS Tuning

Configurations for `virtual memory` and `networking subsystems` are typically configured in the `/etc/sysctl.conf` file (refer to your Linux distribution regarding how to adjust the kernel configuration).

### Virtual memory

In general, the Linux virtual memory system will automatically adjust itself for the system workload. We can make some adjustments to how swap space is handled, as well as to dirty memory pages, to tune these for Kafka’s workload.


