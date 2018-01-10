# MongoDB

A document based database. Natively supports scaling out through sharding feature.

> **MongoDB Compass:** Compass is a GUI client for viewing MongoDB databases and documents they contain. Supports read and write data.
>
> **MongoDB Atlas:** MongoDB as a service.  
> For development purposes, if you use AWS, Atlas gives you 512MB storage free of cost, for a 3 node replica set.  
> [https://www.mongodb.com/cloud/atlas/lp/general](https://www.mongodb.com/cloud/atlas/lp/general)  
> [https://cloud.mongodb.com](https://cloud.mongodb.com)

##### Terms

```
Cluster: an instance of MongoDB
Database: A database servers as a namespace for Collection. Database can have multiple collections.
Collection: Collection stores individual Records. Each datbase & collection combination define a namespace.
Record: Often referred as documents.
Indexes: ?? Related to performance.

Remember:
There is no authorization yet supported on document level, but only database or collection level.
MongoDB supports nesting a document.
```

Scalar Data Types

##### Open questions

```
What percentage of fields have value in a particular column?
What percentage of a certain value is present in a column?
    Since schema tab is missing from Compass. Available in MongoDB Compass 3.4.2 Community Edition.
```



