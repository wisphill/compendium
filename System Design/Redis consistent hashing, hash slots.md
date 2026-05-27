#redis #hashing #consistent-hashing
```table-of-contents
```
### 3 nodes, 1 master 2 slaves 
1. Adding more nodes is just adding more replicas, requires more CPU to sync between nodes.
2. Small volume, HA

### 3 standalone nodes: 
1. (Modulo) Redis library calculates the node for the key by hashing it % number of nodes. When adding one node, this calculation would return different result.
2. (Consistent hashing) Set the library distribution -> consistent: The nodes will be distributed on the hash ring. Requires to enable virtual nodes to separate the data on the big nodes > more smaller virtual ones.
   It Requires more CPUs, nightmare to debug to find where the key is. 
3. Using proxy + (Modulo) / (Consistent hashing) to reduce the number of connections to the Redis.

### Cluster mode
1. Using hash slots, **16,384** slots. $Slot = CRC16(key) \pmod{16384}$.
2. Require at least 3 masters, lots of replicas, so the system is able to vote/elect the master. 
3. Client must support the cluster mode and error MOVED
4. Scaling by moving slots from node to node. More RAM, more CPU, much expensive when having more nodes.

### Problems with Redis
1. Data skew -> Consistent hashing. If using the hashtag, make sure it's tagged by smallest unit (such as userId not big as tenantId). 
   Or just don't use hashtag, no multi keys commands (MGET, TRANSACTION)
2. Migrate to cluster mode from Modulo: 
   - Sync (Redis-Shake) -> Dual-write -> Switch (Zero gap, pause write on Old nodes (few minutes/maintaince)) -> Write only on the Cluster.

