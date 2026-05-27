```table-of-contents
```
## Docker networking
1. Docker will create veth for each container, from host to the container
2. Docker bridge is the virtual router to route packages between container, they can see each others
   Can use custom bridge to isolate some containers
3. Docker SWARM
### Docker Swarm, overlays
1. Control plane: control the networking, IP address, map of networking overlays
2. Create the tunnel, virtual ENI - VXLAN to encapsulate the package to route the package to another host, then go to the veth of the container
3. It's Docker overlays, so all packages has more information, bigger after lots of complicated steps.
   
