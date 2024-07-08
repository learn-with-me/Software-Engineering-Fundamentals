# Consistency

Consistency is the property that ensures that the database remains in a consistent state before and after the transaction.
It is the responsibility of the database to ensure that the data is consistent after the transaction is completed.
Consistency ensures that the data is valid and follows all the rules and constraints defined in the database schema.

- `Consistency in data` means the data is valid and follows all the rules and constraints defined in the database schema. This mostly comes down to the enforcing `referential integrity`, uniqueness, and other constraints.
- `Consistency in reads` means that the data read is the same as the data written by the transaction. This can happen because there are `multiple instances` of the database, and they may be out of sync, and the transaction might read from a different copy than it wrote to.

`Atomicity` and `Isolation` are the properties that `ensure` consistency in the database.
This is because if the transaction is atomic, then all the queries in the transaction must succeed for a transaction to be successful. If one of the queries fails, then all previous queries must roll back. This ensures that the data is consistent.

It is one of the property that was traded off in different database systems to achieve better performance, speed and scalability.
This means that the database might not be consistent at all times, but it will `eventually` become consistent.

## Replication

`Synchronous replication` is a technique used to ensure consistency in distributed databases.
In this technique, the data is written to multiple nodes before the transaction is considered complete.
This ensures that the data is consistent across all nodes.

`Asynchronous replication` is another technique used to ensure consistency in distributed databases.

## Eventual Consistency

`Eventual Consistency` is a consistency model used in distributed systems.
In this model, the system guarantees that if no new updates are made to a given data item, eventually all accesses to that item will return the last updated value.
This model is used to achieve high availability and partition tolerance.
