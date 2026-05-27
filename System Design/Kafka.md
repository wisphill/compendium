#kafka 
```table-of-contents
```
### Basics
1. Same consumer group, 1 consumer takes 1 partition. Other consumers will be treated as IDLE.
2. Should setup worker for the Kafka consumers because it requires different resources as API services. It can be in the same service if the logic is very light.
3. IDLE consumer still causes Kafka rebalancing. Solutions: 1. Separate workers, Increase partitions
4. Partitions of a topic are distributed on each brokers, each brokers will clone the partition based on number of replication factors. A topic has 3 partitions & 3 replication factors, in total, it has 9 partitions.
### Rebalancing
- Consumer dies / restarts - even if it's IDE
- New consumer
- Brokers rebalance

### Topic partition reassignments
- Moving storage from broker 1 -> broker 3 with throttling slowly, step by step. Partitions of topics will be brought from broker 1 -> new broker
- Data still can be read from the broker 1, it is still keeping at least 1 partition.
- Error only when Kafka shutdowns the partitions on old broker > then re-electing the leader for the topic.
- Moving partitions: New partitions (follower) on the broker 3 synchronizes the data with the current leader on the old broker. 
- Prefer to use Cruise control open source of Linkedin

### Cruise Control of Linkedin
- Monitor the Kafka systems, then plan, run better than the topic partition reassignment.

### KRaft/Zookeeper
1. Store the metadata of the clusters: brokers, topics, partitions, configurations
2. KRaft stores the data in the internal Kafka topics. Some brokers are elected to be controllers to sync the metadata.
3. Zookeeper is outdated