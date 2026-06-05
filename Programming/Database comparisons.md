---
modified: Jun 02, 2026
---
#database #comparisions 
```table-of-contents
```
## Terminologies
### 1. Standard consistency & Eventual consistency
- **Standard consistency**: Locking, all or nothing, **lock** during write transaction to **all nodes** and release lock after synchronizing.
- **Eventual consistency**: Priority write first for the primary node, then synchronize to other nodes later. Quick write. The user connects to other nodes can see different data. Usually, it's lock free.

### 2. Lock free with transaction
- On the database side, there is no lock, using **optimistic lock mechanism**. The conflicts only can be detected when writing to the database. When there are too many writes, the database engine will choose which one can write. It can use **Last Write Wins** or **reject the outdated transaction**
- The database uses **CAS (compare and set)** mechanism to compare **the current version of the record** in the database and the **copy version of the record in the transaction**. So the conflicts would be resolved

### 3. Optimistic lock and pessimistic lock
##### Pessimistic lock
- Just locking when the transaction starts using mutex, table lock, row lock. 
- **S LOCK**: Shared lock, engine requires this lock when calling the READ actions (SELECT).
- **X lock**: Exclusive lock, engine requires this lock when calling UPDATE, CREATE actions.
- **Range lock**: Requires this lock to protect a range of data based on the WHERE condition.
**X lock and S lock**
- Both X lock and S lock are applied on the row level, to protect the row.
- The range lock, gap lock, predicted lock are applied on the index, to protect a range. Range lock won't work effectively without the database indexes.
- X lock and S lock are mutual exclusive, if a row are protected by S lock, it cannot apply a X lock, the command requires the X lock will be in the engine queues.
##### Optimistic lock
- Using CAS, check version and retry.
- Better for WRITE

### 4. Isolation levels
Isolation level is applied on the transaction when it's initialized.
##### Types:
1. **READ_UNCOMMITED**: Set the X lock on rows for the lifetime of the transaction (default for most databases). Prevent multiple writes. *All read query in other transaction still can be run because it does not require any S lock.* So the dirty read problem can happen. 
2. **READ_COMMITTED**: Set the X lock for lifetime of the transaction, apply the S lock for all READ query and release immediately after that. So all read queries are **blocked by the uncommitted WRITE**
3. **REPEATABLE READ**: Set the X lock for lifetime of the transaction, Set the S lock for lifetime of the transaction. *Phantom read still can be happened because the lock cannot be applied on the non-existent rows.* 
4. **SERIALIZABLE:** Set the X lock for lifetime of the transaction, Set the S lock for lifetime of the transaction, using range lock, gap lock on the indexes for lifetime of the transaction. Prevent all issues.

### 5. Concurrency Problems
1. **LOST UPDATE**: when the concurrent WRITEs happen.
2. **DIRTY READ**: n transactions, free READ, free WRITE, read uncommitted data. Transaction x got rollbacked, then READ is wrong.
3. **NON-REPEATABLE READ**: 1 transaction, **same READ query for a row** and be called multiple times but return different results for a row
4. **PHANTOM READ**: same as NON-REPEATABLE READ but **for the range of rows**, it's impacted by another transaction.

**Solutions**
1. **LOST UPDATE**: Using CAS, read uncommitted isolation level *(prevent multiple writes)*.
2. **DIRTY READ**: Using read committed isolation level.
3. **NON-REPEATABLE READ**: Using repeatable isolation level.
4. **PHANTOM READ**: Using **Serialized** Isolation Level.

### 6. MVCC & Snapshotting in transaction.

## Comparisons
**RDBMS and NoSQL**
- **RDBMS**: related database, consistent data schema, best for the sensitive business logics (banking, finance, complex JOIN, analytics...) because of the ACID specifications of the RDBMS
- **NoSQL**: Not fully support and have enough ACID specifications. Dynamic schema, faster scaling, for write heavy. 

## Pros/Cons of Database
### MongoDB
- Document type database (JSON/BSON), dynamic schema
- Has ACID, but it's **Eventual consistency**
