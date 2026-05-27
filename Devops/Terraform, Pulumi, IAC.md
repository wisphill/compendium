#terrafor, #iac

**Fix the terraform state**
```
# fixing the terraform state
terraform state rm/pull/push/mv/list/show

# debug, backup
terraform state pull 

# change the backend name only
terraform init -migrate-state

# change the backend, use the new state > re-importing resources
terraform init -reconfigure

# broken state file
terraform init
1. Failed to load backend >>	Backend config / auth
2. Error acquiring the state lock >>	Lock system
3. Invalid state file >>	State bị corrupt
4. NoSuchBucket / ContainerNotFound >>	Storage
5. Digest mismatch / checksum >> State content
```
1. Backup state file before fixing
2. Restore state file if has versioning file
3. Fix manually/ debugging/ fix JSON before checking real content

**For EKS**
1. Simple, several clusters -> Terraform / ArgoCD
2. Dynamic multiple clusters -> Pulumi

**Ignore changes configuration**
When the field can be mutated by other systems beside Terraform and cannot reflect the desired state. Avoid using this for core configs.

**for_each vs count** 
count: indicate by index
for_each: indicate resource by key
count: cause drifts