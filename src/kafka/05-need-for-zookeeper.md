# Need for ZooKeeper

Writes to ZooKeeper are only performed on changes to the membership of consumer groups or on changes to the Kafka cluster itself. This amount of traffic is generally minimal, and it does not justify the use of a dedicated ZooKeeper ensemble for a single Kafka cluster.

Dependency on ZooKeeper is shrinking over time. Administration tools now connect directly to the cluster and have deprecated the need to connect to ZooKeeper directly for operations.

> ZooKeeper-less Kafka is not production-ready yet.

## Other References

- Confluent [Kafka without ZooKeeper](https://www.confluent.io/blog/kafka-without-zookeeper-a-sneak-peek/)
- Hevodata [Kafka without ZooKeeper](https://hevodata.com/learn/kafka-without-zookeeper/)
