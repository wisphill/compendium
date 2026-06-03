---
modified: Jun 02, 2026
---
```table-of-contents
```
### Terminologies
#### Standard consistency & Eventual consistency
**Standard consistency**: Locking, all or nothing, **lock** during write transaction to **all nodes** and release lock after synchronizing.
**Eventual consistency**: Priority write first for the primary node, then synchronize to other nodes later. Quick write. The user connects to other nodes can see different data. Usually, it's lock free.

#### Lock free with transaction
- On the database side, there is no lock, using **optimistic lock mechanism**. The conflicts only can be detected when writing to the database. When there are too many writes, the database engine will choose which one can write. It can use **Last Write Wins** or **reject the outdated transaction**
- The database uses **CAS (compare and set)** mechanism to compare **the current version of the record** in the database and the **copy version of the record in the transaction**. So the conflicts would be resolved

#### Optimistic lock and pessimistic lock
TODO: Update me
### Comparisons
**RDBMS and NoSQL**
- **RDBMS**: related database, consistent data schema, best for the sensitive business logics (banking, finance, complex JOIN, analytics...) because of the ACID specifications of the RDBMS
- **NoSQL**: Not fully support and have enough ACID specifications. Dynamic schema, faster scaling, for write heavy. 

### Pros/Cons of Database
#### MongoDB
- Document type database (JSON/BSON), dynamic schema
- Has ACID, but it's **Eventual consistency**
