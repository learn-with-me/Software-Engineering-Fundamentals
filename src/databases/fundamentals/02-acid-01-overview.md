# ACID

The ACID properties (Atomicity, Consistency, Isolation, Durability) are fundamental principles that aim to ensure the `reliability of database transactions` in relational database systems.
However, the strict adherence to these principles can vary based on the specific requirements of a database system and the `trade-offs` that are acceptable for a given application or context.

## Properties

### Atomicity

Atomicity ensures that all operations within a transaction are completed successfully; if not, the transaction is aborted.

That is, all the queries in a transaction must succeed for a transaction to be successful, since all queries in the transaction are considered to be one unit of work.
Like an `atom`, which cannot be broken apart further. This means, if one of the query fails in a transaction, then all previous queries must roll back.

In the case when the database crashes prior to commit, all the successful queries in the transaction should roll back.

Lack of atomicity leads to `inconsistency` since the money taken out from one account would never make it to another account during a database crash.

### Isolation

Ensures that concurrent execution of transactions leaves the database in the same state that would have been obtained if the transactions were executed sequentially.

Each transaction opens a TCP connection, and there are multiple transactions happening at a time in a database. Hence, there is a chance that multiple transactions can compete to read/write the same piece of data.

This brings up a question: can my inflight transaction see changes made by other transactions?
That depends on the isolation level.

### Consistency

Guarantees that a transaction can only bring the database from one valid state to another, maintaining database invariants.

### Durability

Ensures that once a transaction has been committed, it will remain so, even in the event of power loss, crashes, or errors.

## Flexibility

The ACID properties are not always strictly enforced in all database systems. Some systems may choose to relax these properties to achieve better performance, speed, or scalability.

While these properties are ideal for ensuring `data integrity` and `consistency`, there are scenarios where strict adherence to all ACID properties may not be necessary or could lead to performance bottlenecks.
For example, in highly distributed systems or in scenarios where performance and availability are prioritized over strict consistency, some flexibility is allowed.

Flexibility with ACID:
- **Eventual Consistency**: Some systems may opt for eventual consistency over immediate consistency to improve availability and partition tolerance, relaxing the Consistency requirement.
- **Isolation Levels**: Different isolation levels (Read Uncommitted, Read Committed, Repeatable Read, Serializable) offer flexibility in how transactions are isolated from each other, trading off between performance and the degree of isolation.
- **Performance Optimization**: In some cases, systems might relax durability guarantees (e.g., using delayed writes) to enhance performance, although this is less common because it risks data loss.

In summary, while the ACID properties are a cornerstone of relational database design, practical considerations and the specific needs of applications may lead to variations in how strictly these properties are enforced.
The choice to relax certain ACID properties is a trade-off that needs to be carefully considered based on the application's requirements for consistency, availability, and performance.
