# Configuring Topics

The Kafka server configuration specifies many default configurations for topics that are created, including partition counts and message retention, etc.

The defaults in the server configuration should be set to baseline values that are appropriate for the majority of the topics in the cluster.

> Automatic topic creation is enabled by default

## num.partitions

Determines how many partitions a new topic is created with, defaults to `1` partition.

> The number of partitions for a topic can only be increased, never decreased.

Partitions are the way a topic is scaled within a Kafka cluster, which makes it important to use partition counts that will balance the message load across the entire cluster as brokers are added. It is common to have the partition count for a topic be equal to, or a multiple of, the number of brokers in the cluster. This allows the partitions to be evenly distributed to the brokers, which will evenly distribute the message load.

Refer [Choosing Partitions](../how-to/choosing-partitions.md) for more details.

## default.replication.factor

Replication strategy can vary depending on the desired durability or availability of a cluster.

Below is a recommendation that will prevent outages due to factors outside of Kafka’s internal capabilities, such as hardware failures.

> Set the replication factor to at least 1 above the `min.insync.replicas` setting (abbreviated as RF++). RF++ will allow easier maintenance and prevent outages.

For more fault-resistant settings, if you have large enough clusters and enough hardware, setting your replication factor to 2 above. This is to allow for one planned outage within the replica set and one unplanned outage to occur simultaneously. This would mean you’d have a minimum of three replicas of every partition.

## log.retention.ms

Configuration for how long Kafka will retain messages is by time.

The default is specified in the configuration file using the `log.retention.hours` parameter, and it is set to 168 hours, or one week. However, there are two other parameters allowed, `log.retention.minutes` and `log.retention.ms`. All three of these control the same goal (the amount of time after which messages may be deleted), but the recommended parameter to use is `log.retention.ms`, as the smaller unit size will take precedence if more than one is specified.

Retention by time is performed by examining the last modified time (mtime) on each log segment file on disk. Under normal cluster operations, this is the time that the log segment was closed, and represents the timestamp of the last message in the file.

## log.retention.bytes

Another way to expire messages based on the total number of bytes of messages retained. Note that all retention is performed for individual `partitions`, not the topic. Setting the value to `–1` will allow for infinite retention.

## log.segment.bytes

The `log.retention.*` settings operate on log segments, not individual messages. As messages are produced to the Kafka broker, they are appended to the current `log segment for the partition`. Once the log segment has reached the size specified by the `log.segment.bytes` parameter, which defaults to `1 GB`, the log segment is closed and a new one is opened. Once a log segment has been closed, it can be considered for expiration. A smaller log segment size means that files must be closed and allocated more often, which reduces the overall efficiency of disk writes.

Adjusting the size of the log segments can be important if topics have a low produce rate. For example, if a topic receives only 100 megabytes per day of messages, and `log.segment.bytes` is set to the default, it will take 10 days to fill one segment. As messages cannot be expired until the log segment is closed, if `log.retention.ms` is set to 604800000 (1 week), there will actually be up to 17 days of messages retained until the closed log segment expires. This is because once the log segment is closed with the current 10 days of messages, that log segment must be retained for 7 days before it expires based on the time policy (as the segment cannot be removed until the last message in the segment can be expired).

### Retrieving Offsets by Timestamp

The size of the log segment also affects the behavior of fetching offsets by timestamp. When requesting offsets for a partition at a specific timestamp, Kafka finds the log segment file that was being written at that time. It does this by using the creation and last modified time of the file, and looking for a file that was created before the timestamp specified and last modified after the timestamp. The offset at the beginning of that log segment (which is also the filename) is returned in the response.

## log.roll.ms

Another way to control when log segments are closed. This config specifies the amount of time after which a log segment should be closed.

`log.segment.bytes` and `log.roll.ms` are not mutually exclusive properties. Kafka will close a log segment either when the size limit is reached or when the time limit is reached, whichever comes first. By default, there is no setting for `log.roll.ms`, which results in only closing log segments by size.

### Disk performance when using time-based segments

When using a time-based log segment limit, it is important to consider the impact on disk performance when multiple log segments are closed simultaneously. This can happen when there are many partitions that never reach the size limit for log segments, as the clock for the time limit will start when the broker starts and will always execute at the same time for these low-volume partitions.

## min.insync.replicas

When configuring your cluster for data durability, setting `min.insync.replicas` to 2 ensures that at least two replicas are caught up and `in sync` with the producer. This is used in tandem with setting the producer config to ack “all” requests. This will ensure that at least two replicas (leader and one other) acknowledge a write for it to be successful. This can prevent data loss in scenarios where the leader acks a write, then suffers a failure and leadership is transferred to a replica that does not have a successful write. Without these durable settings, the producer would think it successfully produced, and the message(s) would be dropped on the floor and lost.

However, configuring for higher durability has the side effect of being less efficient due to the extra overhead involved, so clusters with high-throughput that can tolerate occasional message loss `aren’t recommended` to change this setting from the default of 1.

## message.max.bytes

This config limits the maximum size of a message that can be produced, which defaults to 1000000, or 1 MB. A producer that tries to send a message larger than this will receive an error back from the broker, and the message will not be accepted.

> This configuration deals with `compressed message size`, which means that producers can send messages that are much larger than this value uncompressed, provided they compress to under the configured size.

There are noticeable performance impacts from increasing the allowable message size. Larger messages will mean that the broker threads that deal with processing network connections and requests will be working longer on each request. Larger messages also increase the size of disk writes, which will impact I/O throughput. Other storage solutions, such as blob stores and/or tiered storage, may be another method of addressing large disk write issues.
