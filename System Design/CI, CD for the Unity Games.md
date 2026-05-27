### Runners
- Github self-hosted runners (local Window server, local MacMini with XCode)
- Github runner
- EC2 for a cheaper price

### Steps
1. Setup runners
2. Setup Github workflow, trigger build on clicks, Slack/Telegram notification integration. 1 build at a time
3. Feature testing on Android version first
4. Use the actions/cache on the cloud, no need on the local. actions/cache contains assets, ...
5. Optimize the concurrency to avoid duplicated build running at the same time


