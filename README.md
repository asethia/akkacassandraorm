# akkacassandraorm

## Introduction

This is Cassandra ORM mapping library; which can be used along with Akka Actor System to read Cassandra table and prepare resultset in generic way, so JSON response can be sent via REST service with minimal code.

Cassandara table is a list of “nested key-value pairs”. Rows in Cassandra are stored in the form of variable key/value pairs or columns. Each row in a table is referenced by a primary key or a row key. The Primary key indicate one or more columns used to retrieve data from a Table. Few terminologies used in Cassandra w.r.t data organization:

* The Partition Key is responsible for data distribution across your nodes.
* The Clustering Key is responsible for data sorting within the partition.
* The Primary Key is equivalent to the Partition Key in a single-field-key table.
* The Composite/Compound Key is just a multiple-columns key.

First part of Primary Key is partion key(s) and second part is Clustering Key. For example PRIMARY KEY ((key1, key2),key3,key4), in that case key1, key2 are part of partion key and key3, key4 is part of cluster key.

The purpose of partition key is to identify the partition or node in the cluster which stores that row. When data is read or write from the cluster a function called Partitioner is used to compute the hash value of the partition key. 

The purpose of clustering key is to store row data in sorted order. The sorting of data is based on columns which are included in the clustering key. This arrangement makes it efficient to retrieve data using clustering key.

## Entity Query Metadata

The next step is defining meta data for a entity; which will allow 
