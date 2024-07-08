# Durability

Durability ensures that once a transaction is committed, it will remain committed even in the case of a `system failure`.
Durability guarantees that the changes made by a transaction are permanent and will not be lost, however it introduces `latency`.

If the crash happens during the commit the database cannot guarantee durability.
The system is durable only when the commit is successful( the data is fully written to disk).
That is why commit speeds are critical, the faster you can commit the lower the chances of such corruption.

The process of persisting the writes that the clients make to the database to a `non-volatile system storage` is called `write-ahead logging`.
Even if the database crashes, the changes made by the transaction are still available in the log files.
When the database comes back online, it can replay the log files to recover the changes made by the transaction.

## Durability Techniques

### Write-Ahead Logging (WAL)

`Write-Ahead Logging` is a technique used by databases to ensure durability.
In WAL, the database writes the changes to the log file before writing them to the actual data files.

When a transaction is committed, the database writes the changes to the log file and then to the data files.
If the database crashes before the changes are written to the data files, it can replay the log files to recover the changes.

Writing a lot of data to disk is expensive, so databases use a technique called `group commit` to write multiple changes to the disk in a single operation.
The database persists a compressed version of the changes to the log file, known as `WAL Segments`, and then writes them to the disk in a single operation.


### Asynchronous Snapshot

In `Asynchronous Snapshot`, the database writes everything to memory and in the background takes a snapshot of the data and writes it to the disk at once.
This technique is faster than `Write-Ahead Logging` because it writes to the disk in a single operation.

### Append-Only File (AOF)

In `Append-Only File`, the database writes all the changes to a log file (similar to WAL).
When the database starts, it reads the log file and applies the changes to the data files.

This technique is used by databases like Redis.

## Database Implementations

Different databases implement durability differently:
1. **MySQL**: Uses `InnoDB` storage engine that supports `Write-Ahead Logging`.
2. **PostgreSQL**: Uses `Write-Ahead Logging` and `MVCC` (Multi-Version Concurrency Control) to ensure durability.
3. **Redis**: Uses `Append-Only File` to ensure durability.
4. **MongoDB**: Uses `journaling` to ensure durability.
5. **Cassandra**: Uses `commit logs` to ensure durability.
6. **SQLite**: Uses `Write-Ahead Logging` to ensure durability.
7. **Oracle**: Uses `Redo Logs` to ensure durability.

## OS Cache

The `Operating System Cache` is a cache that the operating system uses to store data in memory.
When the database writes data to the disk, it writes to the OS Cache first and then the OS Cache `batch-writes` to the disk.
This is done to improve performance, as writing to the disk is slower than writing to memory.

The problem with that is that the OS will tell the database that the data has been written to the disk, even though it is still in the OS Cache.
The database believes that because the OS has acknowledged the writes, the data is safe.
If the system crashes before the OS Cache writes to the disk, the data will be lost. And it is assumed that the database is not durable.

Most of the applications use OS cache, which may not be fine for databases to use.
`Fsync` OS command forces writes to always go to disk and bypass the cache. This can be expensive, but it ensures durability.

Databases that use Fsync:

1. **PostgreSQL**: Uses `fsync` to ensure durability.
2. **MySQL**: Uses `InnoDB` storage engine that supports `fsync`.
3. **SQLite**: Uses `fsync` to ensure durability.
4. **Oracle**: Uses `Redo Logs` to ensure durability.
5. **Cassandra**: Uses `commit logs` to ensure durability.
6. **Redis**: Uses `Append-Only File` to ensure durability.
7. **MongoDB**: Uses `journaling` to ensure durability.
8. **SQL Server**: Uses `Write-Ahead Logging` to ensure durability.
9. **MariaDB**: Uses `InnoDB` storage engine that supports `fsync`.

Redis gives you the option to choose between `fsync` and `no fsync` to trade-off between durability and performance.
Fsync doesn't have to be used for every write, but it should be used for critical writes or when the system is shutting down.

## Example

Consider a banking application where a user transfers money from one account to another.
The transaction is successful, and the money is deducted from the sender's account and credited to the receiver's account.
If the database crashes before the changes are written to the disk, the changes will be lost.
This is where durability comes into play.
The database ensures that the changes made by the transaction are permanent and will not be lost, even in the case of a system failure.

## Summary

- Durability ensures that once a transaction is committed, it will remain committed even in the case of a system failure.
- Durability guarantees that the changes made by a transaction are permanent and will not be lost.
- The process of persisting the writes that the clients make to the database to a non-volatile system storage is called write-ahead logging.
- Different databases implement durability differently, using techniques like Write-Ahead Logging, Asynchronous Snapshot, and Append-Only File.
- The Operating System Cache is a cache that the operating system uses to store data in memory.
- Fsync OS command forces writes to always go to disk and bypass the cache, ensuring durability.
- Databases like PostgreSQL, MySQL, SQLite, Oracle, Cassandra, Redis, MongoDB, SQL Server, and MariaDB use Fsync to ensure durability.
- Redis gives you the option to choose between fsync and no fsync to trade-off between durability and performance.
- Fsync doesn't have to be used for every write, but it should be used for critical writes or when the system is shutting down.
