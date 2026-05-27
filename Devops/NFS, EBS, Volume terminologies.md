#nfs #ebs #volume #device

### NFS hard mount and soft mount
Hard mount
- Application writes/reads to NFS and got error, it gets stuck forever, it's for data safety, important files, DBS
Soft mount:
- NFS client returns I/O error after few retries. It's for caching, temp data, lead to data corruption

### Terminologies
1. Attach volume: Attach **EBS 100GB** to the EC2 instance device: **/dev/sdf**
2. Mount device: Mount device **/dev/sdf** to the **directory /usr/data**
3. Device is busy: The device is still mounting to a directory.

### EBS
1. Single AZ
2. With K8s, `nodeAffinity` to force pod and EBS to be in the same AZ
3. If it requires multiple AZ for HA > NFS

