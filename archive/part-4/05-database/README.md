# Databases

It is important to choose the right tool for the job. Information below is going to help you understand basics of each tool.

##### Most Popular

```
Top Commercial DB    : Oracle, Microsoft SQL Server, DB2, Microsoft Access, Teradata, Splunk
Top Open Source DB   : MySQL, PostgreSQL, MongoDB, Redis, Cassandra, Elastic Search, MariaDB, Hive, Neo4j
Trending DB: Graph DB & Time Series DBMS

Examples of which DB to use, where and why
```

##### NoSQL

```
NoSQL Database Systems are an alternative to the mainstream Relational DBMS. They don't use a relational data model and
typically have no SQL interface.
The term NoSQL was first introduced in 2009 when many new systems were developed in order to cope with the new
requirements for database management systems at that time. E.g.  Big Data, scalability and fault tolerance for large
web applications.
The acronym NoSQL is often understood as "Not Only SQL", implying that relational systems are a proven technology but
not necessarily the optimal choice for each kind of intended use.

Classifications:
Key-value stores, Wide Column stores, Document stores, Graph DBMS, RDF stores, Native XML DBMS, Content stores,
Search Engines

Advantages:
• Higher performance
• Easy distribution of data on different nodes (e.g. sharding), thereby achieving scalability and fault tolerance
• Higher flexibility by using a schema-free data model.
• Simpler administration
```

### Databases Engine

An initiative to collect and present information on Database Management Systems \(DBMS\). There are gazillion ways to store data as many ways have evolved over time.

##### Relational DBMS

```
Support the relational (table-oriented) data model. The schema of a table (relation schema) is defined by the table name
and a fixed number of attributes with fixed data types. A record (entity) corresponds to a row in the table and
consists of the values of each attribute.
Example: Oracle, MySQL, Microsoft SQL Server, PostgreSQL, DB2
```

##### Key-value Stores

```
The simplest form of DBMS. They can only store pairs of keys and values, as well as retrieve values when a key is known.
These simple systems are normally not adequate for complex applications.
Example: Redis, Memcached, Microsoft Azure Cosmos DB, Hazelcast, Ehcache
```

##### Document Stores

```
Also called document-oriented database systems, are characterized by their schema-free organization of data.
That means:
• Records do not need to have a uniform structure, i.e. different records may have different columns.
• The types of the values ​​of individual columns can be different for each record.
• Columns can have more than one value (arrays).
• Records can have a nested structure.
Example: MongoDB, Amazon DynamoDB, Couchbase, CouchDB, Microsoft Azure Cosmos DB
```

##### Graph DBMS

```
Also called graph-oriented DBMS or graph database, represent data in graph structures as nodes and edges, which are
relationships between nodes. They allow easy processing of data in that form, and simple calculation of specific
properties of the graph, such as the number of steps needed to get from one node to another node.
Graph DBMSs usually don't provide indexes on all nodes, direct access to nodes based on attribute values is not
possible in these cases.
Example: Neo4j, Microsoft Azure Cosmos DB, OrientDB, Titan, ArangoDB
```

##### Time Series DBMS

```
DBMS that is optimized for handling time series data: each entry is associated with a timestamp. For example, time
series data may be produced by sensors, smart meters or RFIDs in the so-called Internet of Things, or may depict the
stock tickers of a high frequency stock trading system.Time Series DBMS are designed to efficiently collect, store and
query various time series with high transaction volumes.
Example: InfluxDB, Kdb+, RRDtool, Graphite, openTSDB
```

##### RDF Stores

```
The Resource Description Framework (RDF) is a methodology for the description of information, originally developed for
describing metadata of IT resources. Today it is used much more generally, often in connection with the sematic web, but
also in other applications.
The RDF model represents information as triples in the form of subject-predicate-object.
RDF stores can be seen as a subclass of graph DBMS, by interpreting the predicate as a connection between subject and
object in the above notation. However, RDF stores offer specific methods that go beyond those of the general graph DBMS.
For example, SPARQL, an SQL-like query language for RDF data, is supported by most RDF stores.
Example: MarkLogic, Jena, Virtuoso, AllegroGraph, GraphDB
```

##### Object Oriented DBMS

```
The goal was to be able to simply store the objects in a database in a way that corresponds to their representation in a
programming language, without the need of conversion or decomposition. Additionally, the relationships between the
objects, e.g. inheritance should also be maintained in the database.
An object oriented DBMS thus follows an object oriented data model with classes (the schema of objects), properties and
methods. An object is always managed as a whole.
Object databases often use their own SQL-like query languages for manipulation of objects.
Example: Cache, Db4o, ObjectStore, Versant Object Database, Matisse
```

##### Search Engines

```
Search engines are NoSQL DBMS dedicated to the search for data content. In addition to general optimization for this
type of application, the specialization consists in typically offering the following features:
• Support for complex search expressions
• Full text search
• Stemming (reducing inflected words to their stem)
• Ranking and grouping of search results
• Geospatial search
• Distributed search for high scalability
Example: ElasticSearch, Solr, Splunk, MarkLogic, Sphinx
```

##### Multivalue DBMS

```
Similar to relational systems - store data in tables. However, other than RDBMSs, they can assign more than one value to
a record's attribute. As this contradicts the first normal form, these systems are sometimes called NF2 (non-first
normal form) systems.
These features should be used in RDBMSs only in special cases, whereas they form the basis for data modeling in
multivalue DBMSs, not least because these systems are not optimized for joins.
Example: Adabas, UniData, UniVerse, jBASE
```

##### Wide Column Stores

```
Also called extensible record stores, store data in records with an ability to hold very large numbers of dynamic
columns. Since the column names as well as the record keys are not fixed, and since a record can have billions of
columns, wide column stores can be seen as two-dimensional key-value stores.
Wide column stores share the chracteristic of being schema-free with document stores, however the implementation is
very different.
This is an internal concept for improving the performance of an RDBMS for OLAP workloads and stores the data of a table
not record after record but column by column.
Example: Cassandra, HBase, Microsoft Azure Cosmos DB
```

##### Native XML DBMS

```
NXD are DBMS, whose internal data model corresponds to XML documents.
They can represent hierarchical data, they understand embedded PCDATA declarations in XML elements, and they support
XML-specific query languages ​​such as XPath, XQuery or XSLT.
Native XML DBMS do not necessarily store data as XML documents, they can use other formats for better efficiency.
Example: MarkLogic, Oracle Berkley DB, Virtuoso
```

##### Content Stores

```
Also called content repositories, are DBMS specialized in the management of digital content, such as text, pictures or
videos, including their metadata.
In addition to the storage and queries, normally using SQL or XPath, features that are typically supported are full
text search, versioning, hierarchically structured content, and access control.
The Content Repository API for Java (JCR) is a standard API for Java-based implementations of content stores.
Example: Jackrabbit, ModeShape
```

##### Event Stores

```
DBMS implementing the concept of event sourcing. They persists all state changing events for an object together with a
timestamp, thereby creating time series for individual objects. The current state of an object can be inferred by
replaying all events for that object from time 0 till the current time.
As an example, for a shopping cart object each insertion of a product (product name, quantity, price) would be persisted
as a new event.
Due to performance reasons many Event Stores realize concepts for holding snapshots (object states at a specific point
in time).
Example: Event Store, NEventStore
```

#### References

```
https://db-engines.com/en/ranking
https://db-engines.com/en/articles
```

#### DB for Local Development

```
https://github.com/typicode/lowdb         # Small local JSON database powered by Lodash
https://github.com/techfort/LokiJS        # In-memory JavaScript Datastore with Persistence
https://github.com/pouchdb/pouchdb        # inspired by Apache CouchDB. Work offline as well.

http://www.sqlitetutorial.net/sqlite-nodejs/connect/
```



