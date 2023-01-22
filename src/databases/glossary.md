# Glossary

## TPS / QPS

`Transactions per second` or `Query-rate per second`. Time to complete a transaction varies based on the operations being performed by the transaction. Hence, TPS is the average count of transactions, a server is capable of processing in a second.

The overall processing capability of the system depends on the minimum TPS value of a system.

```
TPS = (num_of_connections * num_of_concurrent_users) / response_time

If transactions happened sequentially, and in only one thread (on one TCP connection), num_of_connections would be 1, however it is not true in the real world.
```

## Latency

Latency is the time difference between the cause and the effect of a request to a system being observed. It is also known as `lag` in the gaming world. Latency is a consequence of the limited velocity (transmission delay) at which system interactions can propagate. It generally includes one-way delay and round trip delay, measured generally in milliseconds.

Think of a line of people waiting to buy a movie ticket. The line can only move as fast as the person on the counter can process payments and issue tickets to the buyers. Transmission delays happens for the similar reasons. The CPU may be busy handling so many requests that it makes the new requests wait before taking any action on it, for example. Another reason could be that the request is traveling on a high-latency network, and may have nothing to do with the CPU wait.

Measuring `throughput` and `latency` can help to identify performance issues on the network. The intent is to generally to have as much high throughput as possible, and as low latency (quick response) as possible.

### References

- [Latency](https://en.wikipedia.org/wiki/Latency_(engineering)) | Wiki
- [Latency](https://www.hackapedia.com/latency/) | Hackapedia
- [Escaping the DRAM price trap: Storage Class Memory](https://blocksandfiles.com/2018/11/28/2019-the-year-of-storage-class-memory/) | Blocks & Files

## Throughput

The throughput (pressure capacity) of a system is closely related to the CPU consumption of requests, external interfaces, IO, etc. The higher the CPU consumption of a single reqeust, the slower the external system interface and IO impact speed, the lower the system throughput, and vice versa.

Two factors determine the upper limit of throughput:

1. The number of hardware resources available
2. The resource allocation and effective utilization in a system

Important parameters of system throughput: `QPS (TPS)`, `concurrent users`, `response time`.

If the system is overloaded, other consumptions such as context switching, memory, etc cause the system performance to decline.

## RDBMS

Relational Database Management System

