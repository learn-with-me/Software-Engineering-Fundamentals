# Isolation

Each transaction opens a TCP connection, and there are multiple transactions happening at a time in a database. Hence, there is a chance that multiple transactions can compete to read/write the same piece of data.

This brings up a question: can my inflight transaction see changes made by other transactions?
That depends on the isolation level.

## Read phenomena

In the context of `transaction isolation`, `Read phenomena` refer to specific types of `inconsistencies` that can occur when multiple transactions operate on the same data concurrently.
These phenomena are critical to understanding because they directly impact the `integrity` and `consistency` of data within a database.

`Dirty reads` occurs when a transaction is allowed to read data from a row that has been modified by another ongoing transaction but not yet committed.
This means the data being read could potentially be rolled back if the modifying transaction fails, leading to the reading transaction obtaining data that might never be committed or is inconsistent with the database's final state.
To prevent dirty reads, databases use `isolation levels` that define the degree to which the transactions must be isolated from each other, with higher levels of isolation reducing the risk of such phenomena but potentially `impacting performance` due to `increased locking` and `reduced concurrency`.

`Non-repeatable reads` occur in a database when, during the course of a transaction, a row is retrieved twice and different values are obtained each time.
This phenomenon typically happens in a `read-committed isolation level`, where a transaction may see changes made by other transactions that were committed after its start.
This inconsistency can lead to issues in applications that `assume` data will not change during the transaction. 
To prevent non-repeatable reads, a higher isolation level, such as `repeatable read` or `serializable`, can be used.
These levels ensure that once a row is read by a transaction, no other transaction can modify that row until the first transaction is completed.
However, increasing the isolation level can `impact` database performance due to the `increased locking` and `reduced concurrency`.
For example, to solve for this, Postgres updates the row version number every time a row is updated. It never updates the row in place.
While MySQL uses a `read-view` to keep track of the changes made by other transactions.

`Phantom reads` occur in a database when a transaction reads a set of rows that match a certain search condition and then, in a subsequent read within the same transaction, finds additional rows (or fewer rows) that match the condition, due to another transaction's insert or delete operations that are committed in the interim.
This phenomenon is called `phantom` because the new rows seem to appear or disappear unexpectedly, like a phantom.
To prevent phantom reads, a higher isolation level, such as `serializable`, can be used, which ensures that the result set of a query remains consistent throughout the transaction.
However, using higher isolation levels can `impact` database performance due to `increased locking` and `reduced concurrency`.
In case of Phantom reads, we cannot even acquire a lock on the new row because it doesn't exist yet. Hence, we need to lock the range of rows that match the search condition.
Postgres uses `MVCC` to prevent phantom reads.

`Lost updates` occur in a database scenario when two or more transactions read the same data and then update it based on the read value.
If these transactions are executed concurrently without proper isolation, they may overwrite each other's updates without knowing the other transaction's modifications.
This leads to `lost updates`, where the final value in the database reflects only the last write, disregarding the other transactions' updates.
To prevent lost updates, databases implement `locking mechanisms` and `isolation levels`.
`Optimistic locking checks` if the data has changed before committing the transaction, while higher isolation levels, like Repeatable Read or Serializable, ensure that a transaction can detect changes made by others and act accordingly, either by rolling back or retrying the operation.
This can be solved by using `pessimistic locking` where we lock the row before reading it.

## Isolation levels

Isolation levels are a property of a database that defines how transactions interact with each other.
These were introduced to prevent `read phenomena` and to ensure that transactions are executed in a consistent manner.

There are four isolation levels in SQL:
1. Read Uncommitted - No isolation, any change from the outside is visible to the transaction, committed or not. This means you can see dirty reads. It also means that the reads are not repeatable, and fast here.
2. Read Committed - Each query in a transaction sees only the committed data by other transactions. This means you can see non-repeatable reads. This is the default and most popular isolation level in most databases.
3. Repeatable Read - This is the highest isolation level that allows you to see the same data throughout the transaction. This means you can see non-repeatable reads. This is the default isolation level in MySQL.
4. Snapshot - This is a special isolation level that allows you to see the data as it was when the transaction started. It's like a snapshot version fo the database at the moment. This is the default isolation level in Oracle.
5. Serializable - This is the highest isolation level that allows you to see the same data throughout the transaction. This means you can see non-repeatable reads. Transactions run as if they are serialized one after the other. This is the slowest. This is the default isolation level in PostgreSQL.

Each database implements isolation levels differently, and the choice of level depends on the application's requirements for `consistency`, `performance`, and `concurrency`.

## Isolation level implementation

Each DBMS implements isolation levels differently. For example, MySQL uses `read-view` to keep track of changes made by other transactions. While Postgres updates the row version number every time a row is updated. It never updates the row in place.

- `Pessimistic locking` is when we lock (row, table, or page) before reading it, to avoid lost updates. Page-level lock is useful when data is clustered together. Table-level lock is useful when we are doing a full table scan. Row-level lock is useful when we are updating a single row.
- `Optimistic locking` checks if the data has changed before committing the transaction. If the data has changed, then the transaction is rolled back.
- `Repeatable read` locks the row before reading it. This is expensive but useful when we want to prevent non-repeatable reads. Postgres implements RR as snapshot, hence the reason you don't get phantom reads with postgres in RR.
- `Serializable` is usually implemented with `two-phase locking`  or `optimistic concurrency control` depending on the dbms. This is the slowest but the most consistent isolation level. You can implement it pessimistically with `SELECT FOR UPDATE` or optimistically with `SERIALIZABLE` isolation level.
- `Read-view` is a mechanism used by MySQL to keep track of changes made by other transactions. It keeps track of the changes made by other transactions and uses this information to prevent non-repeatable reads.
- `MVCC` (Multi-Version Concurrency Control) is a technique used by databases to allow multiple transactions to read and write data without blocking each other. It creates a new version of the row every time it is updated. This is how Postgres implements isolation levels.

To know if a data is locked, databases have a lock management system. We can use the `pg_locks` table in Postgres.

### Serializable

The `Serializable` isolation level can be implemented using either two-phase locking (2PL) or optimistic concurrency control (OCC), depending on the database management system (DBMS).

- **Two-phase locking (2PL)**: This is a locking mechanism where transactions must first acquire all the locks they need before releasing any. Once a transaction starts to release locks, it cannot acquire any new ones. This strict locking protocol can effectively serialize transactions, ensuring that they execute in a manner equivalent to some serial order. 2PL can be used to implement the `Serializable` isolation level by ensuring that transactions hold read and write locks on all accessed data until the transaction completes, preventing other transactions from making conflicting changes.

- **Optimistic Concurrency Control (OCC)**: This approach assumes that conflicts are rare and does not use locks. Instead, it checks at the end of each transaction to see if any data read or written by the transaction has been changed by another transaction. If a conflict is detected, the transaction is rolled back. OCC can implement the `Serializable` isolation level by ensuring that a transaction can only commit if it does not conflict with any other concurrent transactions, effectively serializing them.

The choice between 2PL and OCC for implementing the `Serializable` isolation level depends on the specific DBMS and its design goals, particularly regarding performance and the expected workload's contention level.

### Serializable vs Repeatable Read

- **Serializable**: This is the highest isolation level that ensures that transactions are executed as if they were serialized, one after the other. This level provides the strongest guarantees for consistency and prevents all read phenomena, including dirty reads, non-repeatable reads, and phantom reads. However, it can be the slowest isolation level due to the increased locking and reduced concurrency.
- **Repeatable Read**: This isolation level ensures that once a row is read by a transaction, no other transaction can modify that row until the first transaction is completed. This prevents non-repeatable reads but may still allow phantom reads. Repeatable Read is less strict than Serializable but provides a good balance between consistency and performance. It is the default isolation level in MySQL.

The choice between `Serializable` and `Repeatable Read` depends on the application's requirements for consistency, performance, and concurrency. `Serializable` is suitable for applications that require the highest level of consistency and can tolerate lower performance, while `Repeatable Read` is a good choice for applications that need a balance between consistency and performance.

Example: Two transactions t1 and t2 are running concurrently. t1 changes all 'a' to 'b', while t2 changes all 'b' to 'a'. If the isolation level is `Serializable`, then only one of the transactions will succeed, while the other will fail. If the isolation level is `Repeatable Read`, then both transactions will succeed, leading to a lost update.

## Example: Isolation levels in PostgreSQL

Let's say we have two transactions, `T1` and `T2`, and they are running concurrently in separate terminals.
    
```sql
-- Terminal 1
BEGIN TRANSACTION;
SELECT * FROM users WHERE id = 1;

-- Terminal 2
BEGIN TRANSACTION;
UPDATE users SET name = 'Alice' WHERE id = 1;
COMMIT;

-- Terminal 1
SELECT * FROM users WHERE id = 1;
COMMIT;
```

In this example, `T1` starts by reading the user with `id = 1`, while `T2` updates the same user's name to 'Alice' and commits the change.
When `T1` reads the user again, it may see the updated name 'Alice' if the isolation level allows it, leading to a non-repeatable read.

Now, to change the isolation level in PostgreSQL, you can use the `SET TRANSACTION ISOLATION LEVEL` command:

```sql
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```

Or

```sql
BEGIN TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```

Repeatable Read is expensive because it locks the row before reading it.
The default in postgres is `READ COMMITTED`, which means you can't see the changes made by other transactions until they are committed.

## Summary

- Isolation levels define how transactions interact with each other in a database.
- Read phenomena, such as dirty reads, non-repeatable reads, phantom reads, and lost updates, can occur when transactions are not properly isolated.
- Isolation levels, such as Read Uncommitted, Read Committed, Repeatable Read, Snapshot, and Serializable, provide different levels of consistency, performance, and concurrency control.
- Databases implement isolation levels using mechanisms like pessimistic locking, optimistic locking, two-phase locking, and optimistic concurrency control.
- The choice of isolation level depends on the application's requirements for consistency, performance, and concurrency.
- Implementing the Serializable isolation level can be done using two-phase locking or optimistic concurrency control, depending on the DBMS.
- Understanding isolation levels is essential for designing database systems that balance consistency, performance, and concurrency.
- Isolation levels are a critical aspect of database transactions and play a key role in ensuring data integrity and consistency.
- The choice of isolation level depends on the specific requirements of the application, balancing consistency, performance, and concurrency.
- Implementing isolation levels involves trade-offs between consistency, performance, and concurrency control, and different databases may use different mechanisms to achieve the desired level of isolation.

## References

* [Isolation (database systems)](https://en.wikipedia.org/wiki/Isolation_(database_systems))
