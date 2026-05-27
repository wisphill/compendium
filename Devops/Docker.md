#docker 
### Secure the Docker against escalation of exploits
1. Using read only container, it won't able to write to the system files
2. seccomp profile: Limit the runnable system commands that the container can run.
3. Turning on User Namespace for the docker config, so it's root only for the container >> if not, root in the container still is the root of the host.
4. Run as non-root user >> for the execution command

### VM and Docker
VM: Copy the whole OS and managed by the Hypervisor
Containerization: Use the same host kernel, has their own namespaces, cgroups (manage limits) and managed by runtime.

### ENTRYPOINT, CMD, RUN
ENTRYPOINT: entry to run command, or passed command
CMD: can be overwritten
RUN: Used in the build time