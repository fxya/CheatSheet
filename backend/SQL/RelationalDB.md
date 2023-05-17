# Relational Database Theory Cheat Sheet

### Tables

- Table: A collection of related data organized in rows (tuples) and columns (attributes).
- Entity: A distinct object or concept represented by a table.
- Attribute: A characteristic or property of an entity.
- Primary Key: A unique identifier for each row in a table.
- Foreign Key: A column in a table that references the primary key of another table.

### Relationships

- One-to-One (1:1): Each row in one table is associated with only one row in another table.
- One-to-Many (1:N): Each row in one table can be associated with multiple rows in another table.
- Many-to-Many (N:M): Multiple rows in one table can be associated with multiple rows in another table. Requires an intermediate table.

### Normalization

- First Normal Form (1NF): Eliminate duplicate data and ensure atomicity by organizing data into tables with unique rows and properly defined columns.
- Second Normal Form (2NF): Satisfies 1NF and eliminates partial dependencies by ensuring that non-key attributes depend on the entire primary key.
- Third Normal Form (3NF): Satisfies 2NF and eliminates transitive dependencies by removing attributes that depend on other non-key attributes.

### Querying

- SELECT: Retrieves data from one or more tables based on specified conditions.
- INSERT: Inserts new data into a table.
- UPDATE: Modifies existing data in a table based on specified conditions.
- DELETE: Removes data from a table based on specified conditions.
- JOIN: Combines rows from two or more tables based on related columns.

### Indexing

- Index: A data structure that improves the speed of data retrieval operations on a database table.
- Primary Index: An index created on the primary key column(s) of a table.
- Unique Index: An index created on a column(s) that enforces uniqueness.
- Composite Index: An index created on multiple columns.
- Clustered Index: Determines the physical order of data in a table.

### ACID Properties

- Atomicity: Transactions are treated as a single unit of work that either succeeds entirely or fails entirely.
- Consistency: Transactions bring the database from one valid state to another.
- Isolation: Transactions are executed in isolation, and their intermediate states are not visible to other transactions until committed.
- Durability: Committed transactions are permanently saved and survive system failures.

### Normal Forms

- Boyce-Codd Normal Form (BCNF): Satisfies 3NF and eliminates all functional dependencies except for those based on the primary key.
- Fourth Normal Form (4NF): Satisfies BCNF and eliminates multivalued dependencies.
- Fifth Normal Form (5NF): Satisfies 4NF and eliminates join dependencies.

### Transactions

- Transaction: A single unit of work that accesses and possibly modifies the contents of a database.
- Savepoint: A marker that defines a point within a transaction that can be rolled back to.
- Rollback: A statement that reverts the database to its state before the beginning of a specified transaction.
- Commit: A statement that finalizes a transaction and allows changes to become permanent.
- Concurrency: The ability of multiple transactions to occur simultaneously without leading to data inconsistency.
- Deadlock: A situation in which two or more transactions are unable to proceed because each is waiting for the other to commit.
- Starvation: A situation in which a transaction is perpetually denied access to a database resource.
- Lock: A mechanism that prevents destructive interaction between transactions accessing the same resource.

### NoSQL

- NoSQL: A database that provides a mechanism for storage and retrieval of data that is modeled in means other than the tabular relations used in relational databases.
- Document Database: Stores data in documents composed of searchable fields mapped to values.
- Key-Value Database: Stores data in key-value pairs.
- Wide-Column Database: Stores data in tables with rows and dynamic columns.
- Graph Database: Stores data in nodes and edges.
- Vector Database: Stores data in vectors (arrays) to allow fast search and analysis of similar items.

### Miscellaneous
- A distributed computer system cannot guarantee all of the following three properties at the same time: Consistency, Availability, Partition tolerance.
- Eventual Consistency: Data will be consistent eventually.
- Sharding: Distributes data across different physical partitions.
- Replication: Stores the same data on multiple machines.