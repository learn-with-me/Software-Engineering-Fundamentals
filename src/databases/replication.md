# Replication

To explain the concept, we're going to be building on a growth story

## Scenario

Let's say you are working on a proof-of-concept application with a need for some form of persistent storage, which has a potential to generate revenue if there are enough users. You anticipate a few hundered users to get on the platform every month. Because there is not enough revenue potential in first year, so you spin up a relational database instance and roll out the application in production.

Based on real-life traffic pattern, you see a growth rate of 5x users per month. As your application starts getting this gradual increase in traffic, you realize that your database is capable of handling 5k queries per second, and this demand will only go up.

### What if I don't do anything?

At soe point, there will be more users than the database can handle. You'll start seeing query latencies go up because the database instance is occupied in receiving queries and putting them in queue to respond back. After some time, some of the queries will start timing out, because they weren't able to finish in time. Increasing timeouts will not help much here, if increasing was even possible. Eventually, the database will crash, some of the transactions in progress will be lost.

### Database restarts

Sure. The database will boot up again, start taking connection requests, and then eventually end up in the same state. Terrible user experience and potentially creating bad reputation with your increased user base.

### Increasing instance size

This is the simplest solution (also called `Horizontal Scaling`), and recommended one without having to increase engineering complexity. You'll just need to be careful that the new instance is up to date, and find a way to avoid downtime when switching traffic between the instances.

#### Challenges

1. Most likely you'll have some down time upgrading the database. Trying to upgrade without downtime can result in risks of data getting out of sync.
2. This is not a highly scalable approach. There is only so much CPU and memory you can add on a single machine. Eventually you'll run out of it all. A good problem to have, but still a problem.
3. Your single database instance is still a single-point-of-failure. A machine can be unavailable for a number of reasons, including hardware failure, network error, power outage, regional outage, etc. You wouldn't want a revenue generating app to have downtime, would you?

### Adding more DB machines

Another approach is to let more than one database machine handle incoming queries (also called `Scaling Vertically`).

If you split the data between those machines, it's called `Sharding`.
If you clone the data across machines, it's called `Replication`.

Not one approach is better than other, just they have very specific use-cases.

If the entire data is too large for a single machine to host, then regardless of how many replicas we add, we're not going to solve the problem of running out of memory. This is where `Sharding` comes in.

Regardless of we shard the data or not, it is a good idea to add more replicas for the following reasons:

- Reduce downtime - be it for scheduled maintenance, server overload, or even node failure
- Improved scalability - a db cluster running with `n` nodes (n > 1), will be capable of running `n + 1` nodes, which becomes a less-effort to no-effort strategy, when there is a need to scale the system.

### But where to send the request?

Now that you have multiple replicas, how would the application know where to send the request or is it the application's responsibility of managing load on database instances equally?

This is achieved by using `DNS` Domain Name Service, which acts as a load balancer in front of the database cluster (example [Amazon RDS](https://aws.amazon.com/premiumsupport/knowledge-center/requests-rds-read-replicas/)).

### Does master use the same load balancer?

Shouldn't be, otherwise how would the application target writes to master?

### What happens to a node that keeps dying?

Will it keep erroring transactions?

## Topics

- Scenario
- Challenge
- What is replication?
- Types of replication
- Single-leader
  - Examples
  - Challenges
- Multi-leader
  - Examples
  - Challenges
- Leaderless
  - Examples
  - Challenges
- Advanced Topics
  - Paxos, 
- What if
  - user growth was overnight insted of gradual?
