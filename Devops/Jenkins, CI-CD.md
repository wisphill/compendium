**Jenkins**
- Controllers - 1 or 0 executors
- Agents using Docker/EC2 - limit number of executors, communicate with controller via SSH or JNLP
- Config: Groovy & Jenkinsfile
- Scaling agents using EC2 plugins > more VMs
- Have mechanism to backup jenkins_home.
- Clean up artifacts by time, monitor the Jenkins memory, GC by using Prometheus

**Jenkins queue**
- Executor configs to avoid too much jobs
- Rate limit 
- HPA by using plugins (K8S/EC2 plugins)

**Jenkins lộ credential**
Revoke token, rotate secrets, check plugin vulnerability

**Scale Jenkins for multiple microservices**
- Centralized pipeline template
- Parallel stages
- Artifact caching

**Cleanup Jenkins**
- Cleanup Artifacts
- Cleanup build history
- Cleanup unnecessary plugins
- Workspace cleanup

**Passing secrets**
- Using withCredential to inject the secret from the credential store
- credential binding plugin

**Freestyle & Multiple branch pipeline**
**Freestyle**: Setup job manually for branch to build >> urgent task
**Multiple branch pipeline**: Automatically create jobs for multiple branches, detect PRs, report status to the Git
For orphaned item strategy to auto cleanup items after x days to save disk space

**Declarative Pipeline & Scripted Pipeline**
Scripted: for complicated logic inside the declarative pipeline, can do anything with Groovy.
Declarative: Strict language >> good support for Blue Ocean to display stages
If logic is duplicated multiple times, can convert it to library.

**Build failed**
- Log checking
- Flaky tests
- Race conditions
- Metrics for node >> resource exhausted


