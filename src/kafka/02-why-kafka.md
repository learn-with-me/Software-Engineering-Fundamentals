# Why Kafka?

Among the many choices for a pub/sub messaging system out there, Kafka can be a good choice because:

## Multiple Producers

Kafka is able to seamlessly handle multiple producers, whether those clients are using many topics or the same topic. This makes the system ideal for aggregating data from many clients and making it consistent. Consumer applications can then receive a single stream of events without having to coordinate consuming from multiple topics.

## Multiple Consumers

Kafka is designed for multiple consumers to read any single stream of messages without interfering with each other client. This is in contrast to many queuing systems where once a message is consumed by one client only. Multiple Kafka consumers can choose to operate as part of a group and share a stream, assuring that the entire group processes a given message only once.

## Disk-based Retention

Durable message retention means that consumers do not always need to work in real time. Messages are written to disk and will be stored with configurable retention rules. This configuration can be applied on a per-topic basis, allowing for different streams of messages to have different amounts of retention depending on the consumer needs. Durable retention means that if a consumer falls behind, either due to slow processing or a burst in traffic, there is no danger of losing data. It also means that maintenance can be performed on consumers, taking applications offline for a short period of time, with no concern about messages backing up on the producer or getting lost. This allows the consumers to restart and pick up processing messages where they left off with no data loss.

## Scalable

Users can start with a single broker, and add tens or even hundreds of brokers to the cluster that grows over time as the data scales up. Expansions can be performed while the cluster is online, with no impact on the availability of the system as a whole. This also means that a cluster of multiple brokers can handle the failure of an individual broker and continue servicing clients. Clusters that need to tolerate more simultaneous failures can be configured with higher replication factors.

## High Performance

Producers, consumers, and brokers can all be scaled out to handle very large message streams with ease. This can be done while still providing subsecond message latency from producing a message to availability to consumers.

## Platform Features

The core Apache Kafka project has also added some streaming platform features that can make it much easier for developers to perform common types of work.

`Kafka Connect` assists with the task of pulling data from a source data system and pushing it into Kafka, or pulling data from Kafka and pushing it into a sink data system.

`Kafka Streams` provides a library for easily developing stream processing applications that are scalable and fault tolerant.

## References

* YT - [System Design: Why is Kafka fast?](https://www.youtube.com/watch?v=UNUz1-msbOM&ab_channel=ByteByteGo)
    * [Why is Kafka fast?](https://blog.bytebytego.com/p/why-is-kafka-fast)
* [How Kafka Is so Performant If It Writes to Disk?](https://andriymz.github.io/kafka/kafka-disk-write-performance/#ssl-and-zero-copy)
* [Maximizing Efficiency](https://kafka.apache.org/26/documentation.html#maximizingefficiency) Official doc