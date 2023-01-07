# Common Configurations

## Topic

| Property                  | Value                 |
| -------------------------- | -------------------- |
| default.replication.factor | 3                    |
| log.retention.ms           | 604800000  // 1 week |

## Broker

| Property                  | Value |
| -------------------------- | ---- |
| TBD                        | TBD  |
| TBD                        | TBD  |

## Configuring retention by size and time

If both values `log.retention.ms` and `log.retention.bytes` are specified, messages may be removed when either criteria is met. For example, if `log.retention.ms` is set to 86400000 (1 day) and `log.retention.bytes` is set to 1000000000 (1 GB), it is possible for messages that are less than 1 day old to get deleted if the total volume of messages over the course of the day is greater than 1 GB. Conversely, if the volume is less than 1 GB, messages can be deleted after 1 day even if the total size of the partition is less than 1 GB. It is recommended, for simplicity, to choose either size-based or time-based retention and not both — to prevent surprises and unwanted data loss, but both can be used for more advanced configurations.

## Coordinating message size configurations

The message size configured on the Kafka broker must be coordinated with the `fetch.message.max.bytes` configuration on consumer clients. If this value is
smaller than `message.max.bytes`, then consumers that encounter larger messages will fail to fetch those messages, resulting in a situation where the consumer gets stuck and cannot proceed. The same rule applies to the `replica.fetch.max.bytes` configuration on the brokers when configured in a cluster.
