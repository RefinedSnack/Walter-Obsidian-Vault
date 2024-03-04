---  
share: "true"  
---  
# CS452: Final Exam Study Guide  
  
```toc  
```  
  
## Database Modeling Concepts:  
  
-   **SQL**: Structured Query Language is a standard language for managing relational databases.  
-   **NoSQL**: Not only SQL, is a non-relational database management system that provides a flexible and scalable approach to data management.  
  
## ACID and BASE:  
  
-   **ACID**: Atomicity, Consistency, Isolation, and Durability. It refers to a set of properties of database transactions that guarantee reliable processing of data.  
-   **BASE**: Basically Available, Soft state, Eventually consistent. It refers to a set of properties of distributed databases that prioritize availability over consistency.  
  
## CAP Theorem:  
  
-   The CAP theorem states that in a distributed system, it is impossible to simultaneously achieve consistency, availability, and partition tolerance.  
-   There is a trade-off between these three dimensions because optimizing for one of them comes at the expense of the other two.  
  
## Basic Data Model:  
  
-   **Key-value**: Stores data as a collection of key-value pairs. Examples include Redis, Riak, and Amazon DynamoDB.  
-   **Document**: Stores semi-structured data as documents in a tree-like structure. Examples include MongoDB and Couchbase.  
-   **Column**: Stores data as columns instead of rows to optimize read-heavy workloads. Examples include Apache Cassandra and HBase.  
-   **Graph**: Stores data as nodes and edges to represent complex relationships. Examples include Neo4j and OrientDB.  
  
## ER Diagram:  
  
-   An Entity-Relationship diagram is a visual representation of entities and their relationships to each other in a database.  
-   It is used to model the structure of a database and to identify the relationships between entities.  
  
## 3rd Normal Form:  
  
-   A table is in the 3rd normal form when it has no transitive dependencies and every non-key column is dependent on the primary key.  
-   This ensures that data is not redundantly stored and minimizes the risk of data anomalies.  
  
## Primary Key/Foreign Key:  
  
-   A primary key is a unique identifier for a row in a table, while a foreign key is a field that refers to the primary key of another table.  
-   The foreign key value is set to null or updated/deleted in accordance with the ON DELETE settings when the primary key is deleted.  
  
## NoSQL Design Principles:  
  
-   NoSQL technologies seek to solve the scalability and flexibility problems of relational databases by prioritizing availability, partition tolerance, and ease of scaling.  
-   They do this by using flexible data models, distributed architectures, and efficient storage mechanisms.  
  
## Sharding:  
  
-   Sharding is a technique used in distributed databases to horizontally partition data across multiple nodes in a cluster.  
-   It allows for increased scalability and fault tolerance by spreading the workload and reducing the risk of a single point of failure.  
  
## Replication Factor:  
  
-   The replication factor determines the number of copies of data that are stored across multiple nodes in a distributed database.  
-   It is used to increase data availability and resilience to node failures.  
  
## Vertical Scalability:  
  
-   Vertical scalability refers to the ability to increase the capacity of a single server or node by adding more resources such as CPU, memory, or storage.  
  
## Horizontal Scalability:  
  
-   Horizontal scalability refers to the ability to increase the capacity of a distributed system by adding more nodes to the cluster.  
  
## CAP Theorem Trade-Off:  
  
-   **MongoDB**: Provides high availability and partition tolerance at the expense of consistency.  
-   **Cassandra**: Provides partition tolerance and high availability at the expense of consistency.  
-   **Neo4j**: Provides consistency and partition tolerance at the expense of availability.  
  
## Consistent Hashing:  
  
-   Consistent hashing is a technique used in distributed systems to evenly distribute data across multiple nodes in a cluster.  
-   It is used in NoSQL systems to allow for dynamic scaling and load balancing.