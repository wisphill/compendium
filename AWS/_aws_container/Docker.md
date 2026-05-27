---
layout: post
description: App are packaged in containers and can be run on any OS. Docker is a software development platform to deploy apps
---
#aws #container #docker

App are packaged in containers and can be run on any OS
Docker is a software development platform to deploy apps
Use cases: Micro-service, lift and shift app from on-premise machine to cloud.
![[Drawing 2023-02-09 22.29.59.excalidraw|600x400]]

### Flow
Dockerfile => build => Docker image => push/pull <=> ECR

### Docker container managements in AWS
1. ECS (Amazon's own container platform)
2. Fargate  (Amazon's own Serverless container platform) (ECS & EKS)
3. EKS (Amazon's managed Kubernetes)
4. ECR

### VM and Docker containers
![[Drawing 2023-02-09 22.37.50.excalidraw |600x400]]

### Docker components
- Docker daemon. Usually installed with `docker` dep.
- Docker engine provider (by native Docker engine, Podman, Colima) to start the docker daemon and connect to host via Docker.sock. When install it on the remote server, consider `docker-ce`
### Best practices for building & creating Docker image
- Use multi stage build to reduce the image size. In the Dockerfile, for e.g we can define multiple of FROM command, a part of Dockerfile is for building and part of Dockerfile is for running script at the minimum dependencies and configurations.
- Use Dockerignore to minimize the files relevant to the build step.
- Minimize the dependencies to reduce the build time and image size
- Decouple the applications into multiple containers
- Leverage build cache to make the Docker build faster
  - Utilize the local/external build cache (s3, Github build cache)
  - Consider to cleanup the build cache by interval by using docker `prune` (image/build)
- Fix version for the Docker image deps

### Dockerfile instructions

| Instruction | Purposes                                                                                                      |
| ----------- | ------------------------------------------------------------------------------------------------------------- |
| FROM        | target the base image for the Dockerfile                                                                      |
| ADD         | add file from host to the container                                                                           |
| COPY        | copy file from host to the container                                                                          |
| ENTRYPOINT  | can be used as default executor of the Dockerfile                                                             |
| CMD         | can be used as default executor of the Dockerfile. But it can be used to be fed as an input of the ENTRYPOINT |
| RUN         | run the command when building the Docker image                                                                |
| VOLUME      | mounted volumes from host or other container to the current Docker container                                  |
| EXPOSE      | export a port to the host environment                                                                         |



