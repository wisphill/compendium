**Deploy 5 services with dependencies?**
- Detect the deploy ordering of services 
- Combine the scripts to deploy the services by orders, combine to wait for health check successfully, wait for service status to be DONE, then deploy the next service.
- If 5 services are in the same instances, running as 5 containers >> with Helm, we can define the container initialization ordering. With ECS, we have dependsOn.

**OOMKilled on prod**
- Make sure the cluster autoscaling works to ensure it has enough space to scale more pods
- Check the RAM and increasing the limit for the pod 
- Mem leak > can restart if needed or considering to rollback
- Check if there is any spike
- Restart services 

**Check issues on prod**
- Combine with checking metrics, logs, trace to find issues
- With EC2 instance, can use dmesg to find if the container is killed by OOM.
- journalctl 
- Check metrics to find spikes 

**Chaos tools**
- Chaos Mesh for K8S to kill a random pod to test the self healing
- Stress test sidecar container to consume the pod RAM.

**Process**
- Check if the issue from app or DB or network
- Stop bleeding to save the system (rollback, restart)
- Finding the root cause & prepare solutions. 