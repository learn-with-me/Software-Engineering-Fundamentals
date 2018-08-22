# Redis

Redis is an in-memory data structure store which can be used as a database, a cache and a message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs and geospatial indexes with radius queries. Simply Redis uses you RAM to store data which is very fast, however if you reboot your server the values are gone, unless you enable _Redis persistence_.

> Good news: by default Redis enables persistence mechanism \(you can disable/configure persistence based on your needs.\)

In order to achieve its outstanding performance, Redis works with an in-memory dataset. Depending on your use case, you can persist it either by dumping the dataset to disk every once in a while, or by appending each command to a log. Persistence can be optionally disabled, if you just need a feature-rich, networked, in-memory cache.

#### Features

* Run atomic operations, like appending to a string; incrementing the value in a hash; pushing an element to a list; computing set intersection, union and difference; or getting the member with highest ranking in a sorted set.
* Supports trivial-to-setup master-slave asynchronous replication, with very fast non-blocking first synchronization, auto-reconnection with partial resynchronization on net split.
* Transactions
* Pub/Sub
* Lua scripting
* Keys with a limited time-to-live
* LRU eviction of keys
* Automatic failover

##### Distribution

Redis distribution/installation comes with Redis Server as well as an in-built Redis Client.

#### References

```
https://hackernoon.com/using-redis-with-node-js-8d87a48c5dd7
```



