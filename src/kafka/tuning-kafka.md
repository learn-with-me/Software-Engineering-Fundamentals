# Kafka Performance Tuning

You don't tune Kafka. You tune the Kafka components.

Your first decision point is - am tuning for `Throughput` or `Latency`?

> TODO: This question needs to be explained since at first it isn't making sense.

## Common Tuning Knobs

Each knob you turn will give and take something.

### Producers

* Acknowledgements, Buffers, Batches
    * Speed vs Data Integrity

### Brokers

* How many nodes and node architecture
    * Speed and Data Integrity vs Cost and Management burden
    * Budgets and SLAs
* Replication factor
* Block sizes (of storage)
* Network thread counts (per CPU)

### Topics

* Number of partitions per node (sweet spot)
    * Speed and Data Integrity vs Cost and Management burden
    * Business priority
    * Architectural decisions

### Consumers

* Commit batching
* Parallelism
    * Speed and Data Integrity vs Cost and Management burden
    * Complexity
    * Monitoring
* Pausing (producers) - when the consuming app is down

## References

* YT | [Best Practices for Monitoring and Improving Kafka Performance](https://www.youtube.com/watch?v=R6OKibnXpBs&ab_channel=Pepperdata)
