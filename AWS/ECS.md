**CloudMap**
For internal service discovery to reduce cost but it has no load balancing feature, when resolving the domain name >> it returns a list of IPs instead.
Pure cloud map needs to care to the TTL for the DNS >> need to retry & timeout at the client side

**AppServiceMesh**
Provide circuit breaker, outlierDetection. 
mTLS between services
client side load balancing to the target.
Health check

**Saga pattern**
Event + rollback/compensation events for the events between services.

**ECS networking**
Bridge: using Docker NAT to talk to the other services, IP is the IP of the EC2, hard for service discovery and use port mapping instead
Host: 1 port per host, because of sharing just one ENI of the EC2
awsvpc mode: 1 task 1 eni (based on size of the instance for the ENI quota)

