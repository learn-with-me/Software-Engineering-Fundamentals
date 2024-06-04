# Database Indexing

`Database indexing` is a data structure technique which allows you to quickly retrieve records from a database. Indexes are used to find data rows with specific column values quickly. Without an index, the database must begin with the first row and then read through the entire table to find the relevant rows: the larger the table, the more costly the operation.

Indexes are special lookup tables that the database search engine can use to speed up data retrieval. Simply put, an index is a pointer to data in a table. An index in a database is very similar to an index in the back of a book.

It's important to note that while indexes can speed up data retrieval, they also have some drawbacks. Indexes take up `disk space`, and they can slow down the `performance` of write operations (INSERT, UPDATE, DELETE) because the index also needs to be updated when these operations are performed. Therefore, it's important to find a good balance and only use indexes on columns that are frequently used in WHERE clauses, JOIN conditions, or ORDER BY clauses.

## Implementations

Database indexes are implemented in various ways depending on the database system. Here are a few examples:

1. **B-Tree Indexes:** This is the most common type of index. B-Tree indexes are used in many databases like MySQL, PostgreSQL, and SQLite. In a B-Tree index, data is stored in a tree-like structure where each node contains a certain number of keys and pointers. The keys act as separation values which divide its subtrees. The left subtree of a key contains values less than the key, and the right subtree of a key contains values greater than the key.

2. **Hash Indexes:** Hash indexes use a hash function to map keys to specific locations in an array. They are extremely fast for exact match lookups but do not support range queries or sorting. Hash indexes are used in databases like MySQL (with MEMORY/HEAP tables) and MongoDB.

3. **Bitmap Indexes:** Bitmap indexes use bit arrays (commonly known as bitmaps) and answer queries by performing bitwise logical operations on these bitmaps. Bitmap indexes are typically used in databases that have low cardinality, i.e., the number of unique values is small compared to the number of records. Examples include Oracle and some versions of MySQL.

4. **Clustered Indexes:** In a clustered index, records themselves are stored physically on the disk in the same sequence as the index. Therefore, there can be only one clustered index on a table. The advantage of clustered indexes is that they are extremely fast for range queries. SQL Server, MySQL, and PostgreSQL use clustered indexes.

5. **Non-Clustered Indexes:** Non-clustered indexes have a structure separate from the data rows. A non-clustered index contains the non-clustered index key values and each key value entry has a pointer to the data row that contains the key value. The pointer from an index row in a non-clustered index to a data row is called a row locator. SQL Server, MySQL, and PostgreSQL use non-clustered indexes.

6. **Multicolumn Indexes (Composite Indexes):** These are indexes that are created on more than one column of a table. The columns are ordered in the index definition as per their priority. PostgreSQL, MySQL, and SQL Server support multicolumn indexes.

7. **Spatial Indexes:** Spatial indexes are used to index spatial data types. They are used to optimize queries that perform operations on geometric shapes in space. MySQL and PostgreSQL (with the PostGIS extension) support spatial indexes.

8. **Full-Text Indexes:** Full-text indexes in MySQL are an index of type FULLTEXT. Full-text indexes can be used only with InnoDB or MyISAM tables, and can be created only for CHAR, VARCHAR, or TEXT columns. A FULLTEXT index definition can be given in the CREATE TABLE statement when a table is created, or added later using ALTER TABLE or CREATE INDEX.

Remember, the type of index used depends on the specific requirements of the database system and the data it is handling.
