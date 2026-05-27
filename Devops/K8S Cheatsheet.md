```
--dry-run=client , draft at the client side, do not create on the API server

k run {{name}} --image={{image_name}} --dry-run=client -o yaml > pod.yaml
k create deployment {{name}} --image={{image_name}} --dry-run=client -o yaml > deployment.yaml
# create service yaml
k expose deployment {{name}} --port=xxx --type=ClusterIP --dry-run=client -o yaml > service.yaml


### Memorize
k run 
k create deployment
k create expose
k create configmap
k create secret
k create job
k create cronjob
k create ingress

pvc: create by writing yaml manually
--dry-run=client -o yaml

--command -- sleep 3600: Use this at the end of the command

### Explain in the short way, at least 3 level of queries
k explain {{resource.pod.xxx}} --recursive 
```

### Resource
```
### Usually, it's a map of 
storage: xxx
cpu: xxx
memory: xxx
```

### Check before switching questions
```
#!/bin/bash

NS=dev
DEPLOY=web-app
SVC=web-svc

echo "=== Checking namespace ==="
kubectl get ns $NS || exit 1

echo "=== Checking deployment ==="
kubectl get deploy $DEPLOY -n $NS || exit 1

echo "=== Checking pods ==="
kubectl get pods -n $NS

POD=$(kubectl get pods -n $NS -l app=$DEPLOY -o jsonpath='{.items[0].metadata.name}')

echo "=== Checking pod status ==="
kubectl get pod $POD -n $NS

echo "=== Checking env var ENV ==="
kubectl exec -n $NS $POD -- printenv ENV

echo "=== Checking config volume ==="
kubectl exec -n $NS $POD -- ls /etc/config

echo "=== Checking service ==="
kubectl get svc $SVC -n $NS
kubectl get endpoints $SVC -n $NS

echo "=== DONE ==="
```
