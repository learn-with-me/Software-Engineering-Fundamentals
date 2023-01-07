# Apache Kafka

Once Java and ZooKeeper are configured, you are ready to install Apache Kafka.

## Installation

The following example installs Kafka in `/usr/local/kafka`, configured to use the ZooKeeper server started previously and to store the message log segments stored in `/tmp/kafka-logs`:

```sh
# tar -zxf kafka_x.xx-x.x.x.tgz
# mv kafka_x.xx-x.x.x /usr/local/kafka
# mkdir /tmp/kafka-logs
# export JAVA_HOME=/usr/java/jdk-xx.x.xx
# /usr/local/kafka/bin/kafka-server-start.sh -daemon /usr/local/kafka/config/server.properties
```

## Verification

Once the Kafka broker is started, we can verify that it is working by performing some simple operations against the cluster: creating a test topic, producing some messages, and consuming the same messages.

Create and verify a topic:

```sh
# /usr/local/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --replication-factor 1 --partitions 1 --topic test
Created topic "test"

# /usr/local/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic test
Topic:test  PartitionCount:1    ReplicationFactor:1     Configs: ........
```

Produce messages to a test topic (use Ctrl-C to stop the producer at any time):

```sh
# /usr/local/kafka/bin/kafka-console-producer.sh --bootstrap-server localhost:9092 --topic test
Test Message 1
Test Message 2
^C
```

Consume messages from a test topic:

```sh
# /usr/local/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
Test Message 1
Test Message 2
^C
Processed a total of 2 messages
```

## Deprecation of ZooKeeper connections on Kafka CLI utilitites

If you are familiar with older versions of the Kafka utilities, you may be used to using a `--zookeeper` connection string. This has been deprecated in almost
all cases. The current best practice is to use the newer `--bootstrap-server` option and connect directly to the Kafka broker. If you are running in a cluster, you can provide the host:port of any broker in the cluster.
