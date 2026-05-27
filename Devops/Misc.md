Cloudflare nên dùng cho HTTP, HTTPS, với websocket cần duy trì quá nhiều connections > not good


### Check bugs
- Is there any new deployment
- Is there any new infra changes?
- Random error? Could be the infra error? Deterministic error? Could be the logic code
- Correlation with the traffic spike? Could be the infra bottleneck

### Rollback
1. Check history, like helm with revision number
2. Rollout tránh downtime, luôn phải có maxUnvailable

### Build platform for dev teams
1. Shared runner with precached Docker with smart buildkit new Engine of Docker (parallel build, cache from multiple sources)
2. Shared pipeline template
3. Enforce via **ECS Task Definition + OPA in CI/CD** open policy agent to check the image manifest or container definition in the ECS
4. Each team has their own repos use the shared pipeline template
### Auto scaling using custom metrics
1. CPU + concurrent user, with the cooldown time for the metric and some hysteresis logic to prevent false alarm. Can be applied for K8S
