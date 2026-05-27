#kafka #exactly-one #delivery
```table-of-contents
```
### Exactly-once semantics (EOS)
1. Requires enabling the idempotency
2. Each producer PID has their own ID
3. Sequence number per PID
4. The broker stores the maximum sequence number that it receives, then the broker accepts the message that has the sequence number is n+1. If not, the messages are rejected but still ACK to the producer
5. Transaction: Begin / Commit / Abort. Included entities are:
	- Transaction Log: Internal topic on the broker
	- TransactionalId: The unique id for the producer even restart
	- Transaction Coodinator: Broker module to control states of the transactions
6. Consumer must be **read_committed**: Only read messages that are committed
7. **At the confluent-kafka-go, if getting OutofOrderSequenceException when sending two batches of messages (A and B, ...), the batch with out of order sequence number would be adjusted then resend. With sarama go, at the moment (9-1-2026), it's considered as fatal error, and won't be succeeded after retries and getting stuck** 

### At most one
It's just fire and forget

### At least one delivery
1. Does no require the idempotency (chống trùng)
2. Send messages and wait for the ACK, if not getting the ACK, just resend it until getting ACK or reaching the max of retries.
