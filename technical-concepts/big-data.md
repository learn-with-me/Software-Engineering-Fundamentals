# Big Data

Big Data SQL is the use of an SQL-like language as the interface to a big data technology.

#### Big Data Storage Engines

| Storage Engine | Description |
| :--- | :--- |
| Cassandra | Cassandra, while a full featured database, is also a popular storage engine for other tools. |
| Flat file | Flat file could mean any flat file storage, such as on disk, HDFS, S3, or equivalent. |
| HBase | HBase is a database that runs on top of Hadoop's HDFS. |
| Hive | Hive is not really a storage engine, however it does project  structure onto data. Hive's data structures are used by a lot of other Big Data tools. |
| RDBMS | Relational databases are often used for storage. |
| RDD | RDD, or Resilient Distributed Datasets, are used by Spark     and can span in-memory or on-disk data. |

#### Big Data SQL

| Tool | Storage |
| :--- | :--- |
| CQL | Cassandra |
| Drill | Flat file, HBase, Hive |
| Hive | Flat file, HBase |
| Impala | Flat file \(HDFS\), HBase |
| Kylin | Hive, HBase |
| Phoenix | HBase |
| Presto | Cassandra, Hive, RDBMS |
| Pulsar | Cassandra, Druid |
| Spark SQL | Hive, RDD |

##### Tools Description \(Storage Engine\)

```
CQL (Cassandra)
CQL is Cassandra's native interface. If you use Cassandra, then CQL is a natural choice.
```

```
Drill (Flat file, HBase, Hive)
Drill allows you to run low latency queries on a variety of data sources including both structured and unstructured data
Choose Drill when your data contains structured and unstructured data or when your schema is rapidly changing.
```

```
Hive (Flat file, HBase)
Hive has two main components: a.) HiveQL, an SQL-like language and b.) Hive as a means of projecting structure on data
files.
Internally, HiveQL converts SQL into Map Reduce. Use HiveQL when you need to run MR jobs, but prefer to avoid writing
MapReduce.
```

```
Impala (Flat file (HDFS), HBase)
Impala, which was created by Cloudera, has its own MPP engine. Choose Impala when you need to run rapidly returning
analytic queries on data stored in Hadoop.
Unlike HiveQL, Impala has its own query engine and does not use MapReduce. Impala is a good option for rapidly returning
queries where your data is spread across HBase and HDFS. However, other query engines are a better choice for long
running queries.
```

```
Kylin (Hive, HBase)
eBay Kylin is a relatively new entrant to the Big Data SQL world. Kylin is very different from the other Big Data SQL
tools.
Kylin adds MOLAP capabilities to Hadoop. If you need to create multi-dimensional cubes on Hadoop data then Kylin is the
natural choice. Under the covers, Kylin uses Hive, MapReduce, and HDFS to create cubes, and uses HBase to store cubes.
```

```
Phoenix (HBase)
Phoenix, created by Salesforce, is a client-embedded JDBC driver that converts SQL into native HBase API calls. Phoenix
is an excellent choice when you need to run rapidly returning queries on HBase.
Phoenix has some overlap with Impala both target rapidly returning queries on HBase. However, Phoenix is a client-side
tool and does not require the installation of a daemon on each data node.
```

```
Presto (Cassandra, Hive, RDBMS)
Facebook Presto provides a unique query capability as it can combine data from multiple storage backends.
Choose Presto when you need to query data that spans multiple storage backends, including a relational database.
Presto uses its own query engine where a Presto worker is installed/runs on each data node.
```

```
Pulsar (Cassandra, Druid)
eBay Pulsar is very different from most of the other Big Data SQL tools. Pulsar is designed to provide an SQL interface
for real-time and stream processing of Big Data.
Pulsar is a stream processing solution, so Cassandra and Druid can be used as storage after data has finishing flowing
through the stream processing pipeline.
```

```
Spark SQL (Hive, RDD)
Spark SQL allows you to use SQL to query RDDs. Choose Spark SQL when you are already using Spark or when you want high
performance queries using Spark's RDDs.
```

##### Resources

```
http://exponential.io/blog/2015/02/26/big-data-sql/
```



