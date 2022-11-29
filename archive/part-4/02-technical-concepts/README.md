# Databases

> Just because you can do it with a language/framework, does not mean you should.

#### JSON

Before we dive into databases, let's understand JSON, as this will drive a lot of decisions on what database to choose and why. Javascript Object Notation \(JSON\) is unstructured, flexible and readable by humans. Basically, you can dump data into the database however it comes, without having to adapt it to any specialized database language \(like SQL\). You can nest fields in a data record, or add different fields to individual data records as and when you need.

All of this makes an important step towards user-friendly computing. Today many prefer JSON over XML. JSON data format is used by a number of NoSQL data stores.

JSON does, however, lack indexing - and JSONB format was created to tackle this problem. JSONB stores data in binary format, instead of a simple JSON blob. Data input is a bit slower, but processing becomes a lot faster since the data doesn't need to be reparsed.

#### Postgres

Able to handle SQL and NoSQL data. Now offers enhanced JSON/JSONB storage capabilities.

Searching for data is faster in here especially when searching for data which is not indexed. PostgreSQL is also faster in sorting.

* selecting without key
* sorting
* complex joins

#### MongoDB

Designed as a native JSON database \(understanding that native JSON databases do not always have the best performance\). NoSQL database systems are great for handling large volumes of unstructured data, at speed. Designed to be agile and scalable. JSONB is referred as BSON in MongoDB world, and limited to 64 bits for representing an integer/floating point.

Creation in document store is faster since there are less constraints and validation. MongoDB performs faster in joins/relations since its a reference to data within the document \(this can be slower if the reference is stored outside of the document\). MongoDB is able to update data way faster that PostgreSQL since latter has to check for foreign-key constraints.

* selecting with key
* inserting
* updating
* referencing

#### Yet to be placed

One of the use case for comparison between technologies is to look for if we have more read-write operations than having to update-delete data.

