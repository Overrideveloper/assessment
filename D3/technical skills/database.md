# Databases

### Expectation
The Developer knows how to optimize database queries using indexes, partitioning, striping and clustering.

### Justification

#### Indexing
Indexing is a method that improves the process and optimize performance of a database query by minimizing the number of location accessed within a disk when a query is processed.

An index or database index is a data structure which is used to quickly locate and access the data in a database table. More like the way a big book would have a content page with list of chapters and the corresponding page to each chapter. So searching for a particular chapter would be faster looking through the content page to locate it's page than scrolling through one page after another. 

Indexes are created using some database columns.

- The first column is the Search key that contains a copy of the primary key or candidate key of the table. These values might be stored in sorted order to speed up access to the corresponding data.
- The second column is the Data Reference which contains a set of pointers holding the address of the disk block where that particular key value can be found.

#### Partitioning
Partitioning is a process of splitting very large database tables into multiple smaller parts to improve maintainability and query performance. By splitting a large table into smaller, individual tables, queries that access only a fraction of the data can run faster because there is less data to scan.

We have two basic types of partitioning:
1. **Vertical Partitioning:** is the act splitting a database table into fewer columns. Choosing to move columns that are not frequently accessed to a different table, or if the table is too large. This type of splitting is also called row splitting (the row is split by its columns). It should be noted that database Normalization follows a similar principle but row splitting goes further to split the table even when the table is Normalized.

2. **Horizontal Partitioning or Sharding:** This is when a set of rows in a large table is moved to a different table. For example, customers with ZIP codes less than 50000 are stored in CustomersEast, while customers with ZIP codes greater than or equal to 50000 are stored in CustomersWest. The two partition tables are then CustomersEast and CustomersWest, while a view with a union might be created over both of them to provide a complete view of all customers.

### Striping
This is a technique for spreading data over multiple disk drives and having been interface and act as a single drive. Striping can speed up operations that retrieve data from disk storage. The system breaks a body of data into units and spreads these units across the available disks.
There are two main types:
1. Single-user striping
2. Multi-user striping


### Clustering
A database is a server that can store, filter and search data. Sometimes a single server is not enough to handle the amount of data or the amount of requests. Then you need a database cluster.

We create a database cluster by having multiple replicas of the database working together, and they should be able to take on similar tasks without having to depend on each other.


