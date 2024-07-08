# Atomicity

Atomicity states that all the queries in a transaction must succeed for a transaction to be successful, since all queries in the transaction are considered to be one unit of work. Like an `atom`, which cannot be broken apart further.

This means, if one of the query fails in a transaction, then all previous queries must roll back.

In the case when the database crashes prior to commit, all the successful queries in the transaction should roll back.

Lack of atomicity leads to `inconsistency` since the money taken out from one account would never make it to another account during a database crash.

Q: Could we have separated credit and debit in two separate transactions?
A: No, because the order of execution matters here. There may be another way to ensure order here though.......
