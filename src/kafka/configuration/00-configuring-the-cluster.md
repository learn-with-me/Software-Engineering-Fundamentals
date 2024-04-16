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

#### Swap Space

Generally, it is best to avoid swapping at (almost) all costs. However Kafka makes heavy use of the system page cache, and if the VM system is swapping to disk, there is not enough memory being allocated to page cache.

One way to avoid swapping is simply not to configure any swap space at all. Having swap is not a requirement, but it does provide a safety net if something catastrophic happens on the system. Having swap can prevent the OS from abruptly killing a process due to an out-of-memory condition. For this reason, the recommendation is to set the `vm.swappiness` parameter to a very low value, such as `1`. The parameter is a percentage of how likely the VM subsystem is to use swap space rather than dropping pages from the page cache. It is preferable to reduce the amount of memory available for the page cache.

#### Dirty Memory Pages

Kafka relies on disk I/O performance to provide good response times to producers. This is also the reason that the log segments are usually put on a fast disk. Set `vm.dirty_background_ratio` value lower than the default of 10. The value is a percentage of the total amount of system memory, and setting this value to 5 is appropriate in many situations.

The total number of dirty pages allowed before the kernel forces synchronous operations to flush them to disk can also be increased by changing the value of `vm.dirty_ratio` to `above` the default of 20 (also a percentage of total system memory). Between 60 and 80 is a reasonable number. This setting does introduce a small amount of risk, both in regard to the amount of unflushed disk activity as well as the potential for long I/O pauses if synchronous flushes are forced.

> It is wise to review the number of dirty pages over time while the Kafka cluster is running under load.

It is also recommended to set `vm.overcommit_memory` to `0`. Setting the default value of 0 indicates that the kernel determines the amount of free memory from an application. If the property is set to a value other than zero, it could lead the operating system to grab too much memory, depriving memory for Kafka to operate optimally. This is common for applications with high ingestion rates.

### Disk

Other than the configuration of RAID if it is used, the choice of filesystem for this disk can have the next largest impact on performance. Most common choices for local filesystems are either `Ext4` (fourth extended filesystem) or `XFS` (Extents File System). `XFS` also has better performance for Kafka’s workload without requiring tuning beyond the automatic tuning performed by the filesystem. It is also more efficient when batching disk writes, all of which combine to give better overall I/O throughput.

### Networking

The kernel is not tuned by default for large, high-speed data transfers. In fact, the recommended changes for Kafka are the same as those suggested for most web servers and other networking applications.

The first adjustment is to change the default and maximum amount of memory allocated for the send and receive buffers for each socket. This will significantly increase performance for large transfers. A a reasonable setting is 128KiB. Keep in mind that the maximum size does not indicate that every socket will have this much buffer space allocated; it only allows up to that much if needed.

In addition to the socket settings, the send and receive buffer sizes for TCP sockets must be set separately. A reasonable setting is 4 KiB minimum, 64 KiB default, and 2 MiB maximum buffer. Based on the actual workload of your Kafka brokers, you may want to increase the maximum sizes to allow for greater buffering of the network connections.