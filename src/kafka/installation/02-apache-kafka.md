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

## Configuring the Broker

The default configuration provided with the Kafka distribution is sufficient to run a standalone server as a proof of concept, but most likely will not be sufficient for large installations. There are numerous configuration options for Kafka that control all aspects of setup and tuning. Most of the options can be left at the default settings, though, as they deal with tuning aspects of the Kafka broker that will not be applicable until you have a specific use case that requires adjusting these settings.

There are several broker configuration parameters that should be reviewed when deploying Kafka for any environment other than a standalone broker on a single server.

### broker.id

Every Kafka broker must have an integer identifier, which is set using the configuration. By default, this integer is set to, but it can be any value. The selection of this number is technically arbitrary, however, it is highly recommended to set this value to something intrinsic to the host so that when performing maintenance it is not onerous to map broker ID numbers to hosts.

### listeners

Older versions of Kafka used a simple `port` configuration, which started Kafka with a listener on TCP port 9092.

The new `listeners` config is a comma-separated list of URIs that we listen on with the listener names. If the listener name is not a common security protocol, then another config `listener.security.protocol.map` must also be configured. A listener is defined as `<protocol>://<hostname>:<port>`.

Specifying the hostname as `0.0.0.0` will bind to all interfaces. Leaving the
hostname empty will bind it to the default interface. Keep in mind that if a port lower than 1024 is chosen, Kafka must be started as root. Running Kafka as root is not a recommended configuration.

### zookeeper.connect

The location of the ZooKeeper used for storing the broker metadata is set using the `zookeeper.connect` configuration parameter. The format for this parameter is a semicolon-separated list of `hostname:port/path` strings. Example value is `localhost:2181`

`/path` - an optional path to use as a chroot environment for the Kafka cluster. If it is omitted, the root path is used.

If a `chroot` path (a path designated to act as the root directory for a given application) is specified and does not exist, it will be created by the broker when it starts up.

### log.dirs

Kafka persists all messages to disk, and these log segments are stored in the directory specified in the `log.dir` configuration. For multiple directories, the config `log.dirs` is preferable. If this value is not set, it will default back to `log.dir`. `log.dirs` is a comma-separated list of paths on the local system. If more than one path is specified, the broker will store partitions on them in a “least-used” fashion, with one partition’s log segments stored within the same path. Note that the broker will place a new partition in the path that has the least number of partitions currently stored in it, not the least amount of disk space used, so an even distribution of data across multiple directories is not guaranteed.

### num.recovery.threads.per.data.dir

