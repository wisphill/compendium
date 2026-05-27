#architecture #networking #dnat #snat 

```table-of-contents
```
![[Kubernetes | 800x800]]


### Etcd - protecting the brain
1. Always run at least 3 master nodes, avoid corrupted data
2. Backup /etcd hourly
3. Use etcdctl to restore /etcd from the snapshot
4. Restart kubelet on the control plane

### StatefulSet deployment failed
1. Change the `updateStrategy` to `OnDelete` to avoid deployment deleting running pods
2. Data corruption (new/old version) >> Restore data >> rollback
3. No data corruption >> Able to rollback 
4. Check the crash reason if it's able to be fixed.

### Bottleneck at the Ingress
1. HPA, VA: DaemonSet 1 pod/1 node (Mostly for production) `externalTrafficPolicy: Local` => Traffic to the LB go directly to the ingress without switching nodes.
2. Offloading work >> static content -> CDN
3. Kernel tunning: Increase worker connection, keep-alive >> reduce connection creation.
4. Use NLB, TLS termination at Ingress only

### SNAT, DNAT and Encapsulation IP
Package -> ALB -> Node A (random) -> No Ingress -> SNAT (change source IP to node A IP), DNAT (desc IP of node A to ClusterIP of Service Ingress) -> Node B (ingress) -> routing -> backend process 

### StatefulSet + Headless services
Headless service: A service with no IP, use DNS only to assign to pod.
StatefulSet: manages stateful application with unique pod ID, strict ordering deployment increasing from 0. 

### Downward API
Downward API: a mechanism to get the pod metadata/node metadata from the pod itself by passing these information to the pod env by volume file
API server: Get metadata by accessing REST APIs in the K8S

### **Volume in K8S**
Volume types:
1. emptyDir: A separated volume for each container, can be destroyed when pod is down
2. hostPath: A separated volume on the node
3. persistentVolume: that lives on the cloud, to persist data without impacting by the pod/node lifecycle
4. persistentVolumeClaim: claim amount of volume for the pod
	accessMode: readWriteOnce, readWriteMany
5. storageClass: Auto create cloud storage on the GCloud, AWS

### **Config & Secrets**
1. Can be passed directly to the container
2. Or create config/secret resource on K8S and bind to the containers.
3. Secrets on K8S are just base64 encoded resources.

### **Taint and tolerations**
Node has a taint value, pod has no toleration cannot be lived on that node.
Taint effect: 
	NoSchedule: no new pods with no toleration can be deployed
	NoExecute: kill all pods with no toleration
	PreferNoSchedule: If there are no available nodes, pods can be deployed there

### **Affinity, Anti Affinity, topologyKey**
Node selectors: A property of the pod, to select nodes to deploy. If there are no suitable nodes, cannot deployed
Node affinity: Prioritize nodes has information defined by the affinity. If there are no suitable nodes, deploy to other nodes.
Pod affinity - who do you want to be closed with? Prioritize to pods next together in the same node by using matching labels.
topologyKey: How close are they? - the same AZ, same node or same region. 
Anti affinity: Increase HA of the service, make sure pods are distributed scatteredly.

### **Managing resources for pod in K8S**
**Resource quota**: Quota CPU/RAM/PV for whole namespace
**LimitRange**: Resource limitation for containers/pod in a namespace
**requests/limit**: request - minimum resource allocated for the pod, limit if CPU/RAM is over than request, it will lend some resource from the node. If the RAM is over than limit > OOM
**QoS classes**: 
	Guaranteed: requests = limits 
	Burstable: at least one container has requests < limits
	Best effort: no request limits (first priority to be killed when the node is out of resources)

### Networking - Network policies in advance
1. By default, pod cannot connect to the other applications in the same node by using localhost within its closed network. When enabling the bridged network, it can connect to the other app via container network interface. By using hostNetwork: true *(container config)*
2. **Enable hostPID & hostIPC** *(container config)*: to see/list, communicate via IPC with other apps in the node.
3. **Container security context** *(container config)*: Prevent container to run with non-root, run with privileged mode, prevent container to write fileSystem. 
4. **PodSecurityPolicy** *(cluster resource)*: A cluster resource to avoid user to define the pod to run with root, privileged mode > Now it's outdated > **Pod Security Admission** to force user to follow the best security practice combined with using OPA to validate the pod.
5. **NetworkPolicy** *(cluster resource)*: Isolate traffic pods within the namespace, across namespaces by controlling the ingress, egress traffic.

### RBAC, Service Account, User, API server security
**Service account** *(namespace resource)*: To use for pod to authentication and authorization to interact with the K8S API server
	- Bind SA to pod >> K8S creates token for the SA >> token is mounted to the pod.
	- RBAC via SA
	- Add secrets to the SA to support pull images from private images repo.
**RBAC**: enabled by default, add roles to SA, user for the purpose of accessing to K8S API server
	- Roles: define to access namespace resources
	- ClusterRoles: access cluster resources
	- RolesBinding: bind namespace resources to the user/SA
	- ClusterRolesBinding: bind cluster resources to the user/SA
	- non-resourceUrls: allowed for all to access by default
**Default cluster roles**: 
	- view, edit, admin, cluster-admin: admin can edit Role, Binding, Secret on a namespace. cluster-admin: TOAA
	- system cluster role: for the internal component like kube-scheduler

### Automatic scaling pods, cluster
**HPA** *(namespace resource)*: scale number of pods
**VPA** *(namespace resource - plugins)*: scale size of pods
**Cluster Autoscaler**: scale number of nodes
**Metrics**: CPU, RAM, number of queue messages.