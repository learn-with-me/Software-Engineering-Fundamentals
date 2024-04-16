# Kafka Producers

Kafka ships with `built-in client` APIs that applications interact with. In addition to the client, Kafka has a `binary wire protocol`, which enables applications to read/write messages from/to Kafka by sending the correct byte sequences to Kafka's network port. [Third-party clients](https://cwiki.apache.org/confluence/display/KAFKA/Clients) also implement the wire protocol in language of choice.

Regardless of the business use-case, producer is the one that sends message to Kafka, as desired. And each use-case may have diverse set of requirements:

- Is every message critical, or can we tolerate loss of messages?
- Are we OK with accidentally duplicating messages?
- Are there any strict latency or throughput requirements we need to support?

Example, it would never be ok to accidentally duplicate a credit card transaction or tolerate its loss. On the other side, link click information for a website may tolerate some percentage of losses or duplicates, without worrying about latency.

## High-level Overview

![Kafka Producer Components](./assets/kafka-producer-components.png)

1. The producer accepts a ProducerRecord object. Once we send the `ProducerRecord`, producer will serialize key-value to byte arrays so they can be sent over the network.
2. If no partition is specified, the data is sent to the `Partitioner`, usually based on the key.
3. Now that the producer knows which topic and partition the message will go to. It adds the message to a `batch of records` for that specific partition.
   1. A `separate thread` is responsible for sending these batches of records to the appropriate Kafka broker.
4. On receiving a message, the broker sends back a response.
   1. On `success` - returns `RecordMetadata` object with the topic, partition, and the offset of the record within the partition
   2. On `failure` - returns an error to the producer. The producer may retry a few times, depending on the configruation, before giving up and returning error to the application.

## Configuration

- `bootstrap.server` - a comma-separated list of brokers (`host:pair`) to establish the `initial connection` to the Kafka cluster. The list doesn't need to include all the brokers, since the producer gets all the information from the connection. But it is recommended to have at least 2 to avoid a single point of failure.
- `key.serializer` - name of the class (one that implements `org.apache.kafka.common.serialization.Serializer` interface) to convert the key to byte array. This value is required even if key is optional (use `VoidSerializer` in that case).
- `value.serializer` - Same as for key, but applying on value

For more configurations, refer [here](https://kafka.apache.org/documentation.html#producerconfigs)

## Primary methods of sending message

1. `Fire and Forget` - send a message to the server and not care if it arrived successfully or not. Producer still retries in case of failure, however the message can get lost in case of nonretriable errors or timeouts, and there is no way for the application to log error/exception
2. `Synchronous send` - technically, the producer is always async, however when we `send()` the message, we use `get()` to wait for the promise to be resolved before sending the next record.
3. `Asynchronous send` - we call the `send()` method with a `callback` function to capture the response asynchronously

> Note: a producer object can be used by single thread as well as multiple threads to send messages.

When the producer object sends `ProducerRecord` object using `send()` message, the message will be placed in a buffer and will be sent to the broker in a separate thread. The send() method returns a Java `Future` object with `RecordMetadata`, but since we simply ignore the returned value, we have no way of knowing whether the message was sent successfully or not.

Producer can also encounter errors before sending the message to Kafka, like `SerializationException`, `BufferExhaustedException` or `TimeoutException` when buffer is full, `InterruptException` if the sending thread was interrupted. 

### Synchronous way

The main trade-off involved in sending message synchronously is performance. Brokers can take anywhere from 2ms to a few seconds to respond to producer requests. When sending messages synchronously, the sending thread will spend this time waiting and doing nothing else, not even sending additional messages. This leads to very poor performance (not preferred).

### Asynchronous way

Suppose the network round-trip time between our application and the Kafka cluster is 10 ms. If we wait for a reply after sending each message, sending 100 messages will take around 1 second. On the other hand, if we just send all our messages and not wait for any replies, then sending 100 messages will barely take any time at all.

## Errors

Kafka producer has two types of errors.

### Retriable Errors

Retriable errors are those that can be resolved by sending the message again. The producer can be configured to retry for those erros automatically.

For example, a connection error can be resolved because the connection may get reestablished. A “not leader for partition” error can be resolved when a new leader is elected for the partition and the client metadata is refreshed.

### Non-Retriable

Some errors cannot be resolved by retrying. In such cases, the producer will not attempt a retry and return the exception immediately.

For example, "Message size too large."

## Configuring Producers

Many configurations have reasonable defaults. Some of the parameters have significant impact on memory usage, performance, and reliability of the producers. Hence, setting them manually based on application needs can be extremely helpful.

### Required Parameters

- bootstrap servers
- serializers

### Performance Parameters

`client.id` is a unique logical identifier for the client, used by the brokers to identify messages sent from the client. It is used in logging, metrics and quotas.

`acks` controls how many partition replicas must receive the record before the producer can consider the write successful (default is async). This option has significant impact on the durability of written messages. Choosing acks really means you trade off between reliability and producer latency.

* acks=0    - No acknowledgement from the broker. Fast, but messages can get lost if something goes wrong with the broker. Producer can send messages as fast as the network can support.
* acks=1    - Waits for acknowledgement from the leader broker. Producer retries `X times` on failure, `avoiding potential` data loss. Message can still get lost if leader crashes and last messages were not replicated before that.
* acks=all  - Safest mode. Waits for acknowledgement from the leader broker and all replicas. Latency keeps increasing as the number of acks keep increasing.

> Note: `end-to-end latency` is measured from the time a record was produced until it is available for consumers to read and is identical for all three options. The reason is that, in order to maintain consistency, Kafka will not allow consumers to read records until they are written to all in sync replicas. Therefore, if you care about end-to-end latency, rather than just the producer latency, `there is no trade-off to make`.

## Instantiating Producer

Once we instantiate a producer instance:
1. can we create more than one instance in an application?
2. what are the downsides if any, or things to watch for?
3. Can I have multiple producer instances with different serializers?
4. Retriable and Nonretriable errors and timeouts
5. Why do we need to wait for `get()`, and not use the future object RecordMetadata.

## TBD Index

- Create KafkaProducer
- Create ProducerRecord
- send records to Kafka
- Handle errors that Kafka may return
- Configuration options to control producer behavior
- Partitioning methods
- Serializers
- Custom serializers and partitioners

## Wire Protocol

- [https://cwiki.apache.org/confluence/display/KAFKA/A+Guide+To+The+Kafka+Protocol](https://cwiki.apache.org/confluence/display/KAFKA/A+Guide+To+The+Kafka+Protocol)
- [https://kafka.apache.org/protocol.html](https://kafka.apache.org/protocol.html)
- [https://en.wikipedia.org/wiki/Wire_protocol](https://en.wikipedia.org/wiki/Wire_protocol)

## Tooling

- [https://kafka.js.org/docs/getting-started](https://kafka.js.org/docs/getting-started)
- [https://github.com/SOHU-Co/kafka-node](https://github.com/SOHU-Co/kafka-node)
- [https://docs.confluent.io/platform/6.0.4/tutorials/examples/clients/docs/nodejs.html#consume-records](https://docs.confluent.io/platform/6.0.4/tutorials/examples/clients/docs/nodejs.html#consume-records)
- [https://www.npmjs.com/package/kafka-console](https://www.npmjs.com/package/kafka-console)
- [https://github.com/strimzi/strimzi-kafka-bridge](https://github.com/strimzi/strimzi-kafka-bridge)
