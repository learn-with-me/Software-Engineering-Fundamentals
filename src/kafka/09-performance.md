# Performance Considerations

## Write Efficiency

For efficiency, messages are written to Kafka in batches, all of which are `produced to the same topic and partition`, saving network round trips.

This is really a trade-off between latency and throughput: the larger the batch, the more messages can be handled per unit of time.

Batches are typically compressed to provide more efficient data transfer and storage at the cost of some processing power.
