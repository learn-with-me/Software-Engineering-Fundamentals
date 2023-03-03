# Kafka Monitoring

It all comes down to:

1. Do I know which metrics to monitor?
2. Do I know knobs to turn if I need to tune things relative to each of these performance metrics?

To get these answers, here is what you do:

1. Monitor and observe Kafka performance, throughput and latency
2. Automatically detect and alert on Kafka issues maintaining data integrity
3. Automatically detect threshold, component, hardware degradation and failures
4. Forecast Kafka performance and capacity trends and needs over time.

## Key Metrics

### The Big 4

1. Number of active controllers should always be 1
2. Number of under replicated partitions should always be 0
3. Number of offline partitions should always be 0
4. Consumer lag should be under control (varies by use-case)

### Producer

`Production rate` - when a message leaves a producer, it is typically not on its own. It's been batched with other messages. Production rate is about:

* how big is that batch size?
* how long is it buffered on the producer before being sent?
* what's the network latency between the producer and the broker?
* what's the throughput from producer to the broker?
* were there any failures?
* how often are you acknowledging those packets that were sent?

All these are a potential gating factor in getting the message(s) from the producer over to the broker.

### Broker

* Component health (topics and hardware)
* Load skew
* Capacity
* how many leaders per broker am I actually running?

### Topic

* is partition healthy?
* are we fully replicated?
* are we evenly distributed among the hardware we have? (load skew)
* are topic priorities set based on most important topic (if applicable)?

### Consumer

* are the consumers online?
* is there consumer lag?
* consumption rate & trends

### Beyond the obvious

* Log flush latency
* Messages per second / bytes per second thresholds
* Available network processor / request handler bandwidth
* Topic status metwork throughput
* Open file handles
* Memory, Load
* Disk usage
* GC pauses
* Heap usage
* Swapping
* Dropped packets

## Trends to watch

* Rate of topic growth
* Is TTL on data (retention) long enough for data safety margins, but not too long?
* Is the hardware keeping up with Kafka? - (CPU, Memory, Network and total I/O capcity)

## References

* Kafka uses `Yammer Metrics` for metrics reporting in the server. For more on monitoring, refer kafka [official documentation](https://kafka.apache.org/documentation/#monitoring).
* AWS MSK [metrics details](https://docs.aws.amazon.com/msk/latest/developerguide/metrics-details.html)
