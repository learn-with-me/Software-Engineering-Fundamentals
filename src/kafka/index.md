# Kafka

Kafka is going to be the main focus of this section, while also explaining general concepts.

# TODO Kafka Outline

- [ ] Observer
- [ ] Event Bus
- [ ] Pub-Sub
- [ ] Message Broker

## Index

- [Publish/Subscribe Messaging](./01-pub-sub-messaging.md)
- [Why Kafka?](./02-why-kafka.md)
- [Kafka use-cases](./03-kafka-use-cases.md)
- [Terms Explained](./04-terms.md)
- [Installation](./installation/index.md)

## History

Kafka was originally developed by Jay Kreps, LinkedIn, later released as an open source project on GitHub in late 2010. As it started to gain attention in the open source community, it was proposed and accepted as an Apache Software Foundation incubator project in July of 2011. Apache Kafka graduated from the incubator in October of 2012.

LinkedIn continues to maintain several, including [Cruise Control](https://github.com/linkedin/cruise-control), [Kafka Tools](https://github.com/linkedin/kafka-tools), [Kafka Monitor](https://github.com/linkedin/kafka-monitor), and [Burrow](https://github.com/linkedin/Burrow). In addition to its commercial offerings, Confluent has released projects including [ksqlDB](https://ksqldb.io/), a schema registry, and a REST proxy under a community license (which is not strictly open source, as it includes use restrictions).

In the fall of 2014, Jay Kreps, Neha Narkhede, and Jun Rao left LinkedIn to found Confluent, a company centered around providing development, enterprise support, and training for Apache Kafka. Confluent, through a partnership with Google, provides managed Kafka clusters on Google Cloud Platform, as well as similar services on Amazon Web Services and Azure. One of the other major initiatives of Confluent is to organize the Kafka Summit conference series.

## Message Queue vs Message Bus

There is a lot of overlap in the terms that we use today, in the modern world. They’re all similar: they share similar interfaces (sending and receiving events); they share many features; and they’re both used in complex products or at scale. While similar, they’re (typically) used for different purposes.

A typical queue receives events, buffers them (typically persistently), and allows a worker to read from the queue to process the events. It gives you:

1. Ordering
2. Coupling
3. Pull-based
4. Retries

A typical message bus (or, message broker, event bus, or event broker) also accepts events to be received by other services, though they’re different than queues. Within a message broker, you typically send events to a ‘topic’ (instead of a queue) which is then received by one or more services — unlike a single service within a queue. It gives you:

1. Fan out
2. Delivery guarantees
3. Real-time distribution
4. Scale

## References

- [Kafka: The Definitive Guide](https://www.amazon.com/Kafka-Definitive-Real-Time-Stream-Processing/dp/1492043087) (book)
- [Kafka in Action](https://www.amazon.com/Kafka-Action-Dylan-Scott/dp/161729523X/) (book)
