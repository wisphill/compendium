#istio 
```table-of-contents
```
# TODO - Helm

How to generate Github token?

How to setup the Terraform with any cloud provider

Step to create EKS clusters

**Apache, Nginx**
Nginx: single threaded, event loop, worker will process another event if it has to wait for blocking I/O. Global config on the startup time.
Support load balancing, multiple servers configs.

Apache: 1 process, 1 thread, 1 requests. It's suitable for sessions. It has separate htaccess for each folder, to be setup/read/parsed every requests.

. How to use any load balancer in Ingress controller? How to configure? what are the steps ?




NodePort, ClusterIP


# Istio
## Use cases
1. Canary release, blue-green, A-B testing: Running pods based on subsets, pod can be tagged with version label corresponded with each subset.
2. Branch-based preview environments: 
	Example: Istio: 10 pods - 10 versions - 10 deployemnts
	1 service for 10 pods
	Istio virtual service routing: Branch host header based routing
	With Gitops, use the ApplicationSet of ArgoCD to generate resource based on the Git repo (branch) -> New added deployment, new routing, new destination rule
3. Replace for the K8S Ingress (path,host basic routing)
4. Distributed tracing right after requests go in the cluster
	Envoy Proxy (gateway) -> generate trace Id
	Envoy -> sending Telemetry data (metrics/trace/logs) -> Jaeger/Prometheus
	Tracing nội bộ (In-app Spans) -> Jaeger/Prometheus *(not go through the Envoy)* 
5. **Support internal service MTLS** (Zero trust), it uses the internal certificates managed by the **istiod**.
6. **Locally load balancing**: Prioritize sending pod-pod traffic in the same AZ -> optimizing cost.
7. **Circuit breaker:** Prevent breaking system duel to high volume of traffics. Reject other requests if the service is overloaded. (Protecting the old database if too many connections)
## Traffic debugging
1. Use management app - Kiali -> find which path of traffic is wrong
2. Jaeger: Check by traceId -> find the errored span 
	App span -> Logic
	Envoy span: Network, Circuit breaker, Timeout
3. Check the envoy logs: kubectl logs <tên-pod> -c istio-proxy
4. Check the yaml configuration proxy status: istioctl proxy-status (SYNCED or not)
5. Most errors come from
	Wrong configuration (wrong label, port)
	App does not forward headers

# Traffic spreading in K8S
1. Default: Spread traffics between AZs
2. Network topology mode: Auto >> Prioritize local traffic to the pod in the same AZ, if there are no pods in the same Az >> Find pods in another AZ
3. Network topology mode: Local >> Force traffic in the same node >> only for DaemonSet
4. Network topology mode: Auto >> Break load balancing >> Prefer to use the Istio locally prioritization. 

