# Postgres

PostgreSQL, often simply Postgres, is a general purpose and an object-relational database management system. the most advanced open source database system, with an emphasis on extensibility and standards compliance.

PostgreSQL requires very minimum maintained efforts because of its stability.  Therefore, if you develop applications based on PostgreSQL, the total cost of ownership is low in comparison with other database management systems.

### Features

* User-defined types
* Table inheritance
* Sophisticated locking mechanism
* Foreign key referential integrity
* Views, rules, subquery
* Nested transactions \(savepoints\)
* Multi-version concurrency control \(MVCC\)
* Asynchronous replication
* Recent versions now support
  * Native Microsoft Windows Server version
  * Tablespaces
  * Point-in-time recovery

### Why Postgres?

PostgreSQL is the first database management system that implements multi-version concurrency control \(MVCC\) feature, even before Oracle. The MVCC feature is known as snapshot isolation in Oracle.

### Structure

Postgres shares structural hierarchy with lot other database systems

* Database Server
  * Databases
    * Schemas
      * Tables
      * Views
      * Procedures

#### Rules vs Triggers

Many things that can be done using triggers can also be implemented using the PostgreSQL rule system. One of the things that cannot be implemented by rules are some kinds of constraints, especially foreign keys. It is possible to place a qualified rule that rewrites a command to NOTHING if the value of a column does not appear in another table. But then the data is silently thrown away and that's not a good idea. If checks for valid values are required, and in the case of an invalid value an error message should be generated, it must be done by a trigger.



