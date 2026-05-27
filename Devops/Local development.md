#local-development #local
### Mechanisms
- Dockerfile -> build and run local micro-service image
- VPN for DB
- Local docker/stack for Redis, MSK, SQS
- Internal network testing/demo: Tailscale 
- To access self-hosted Redis on K8S: K8S port forwarding > Create a tunnel from local machine to the targeted service on the K8S to expose the port to the local machine. 