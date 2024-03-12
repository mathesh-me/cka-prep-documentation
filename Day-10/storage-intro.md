## Storage Introduction

### Docker container Storage

- Normally the data inside the container is not persistent. If the container is deleted, then the data inside the container will also be deleted.
- To avoid this, We will use persistent storage for the containers.
- In docker to use persistent storage, we can use the `-v` option to mount the volume to the container.
- Or we can also use `--mount` option to mount the volume to the container.

### Volume driver plugins in Docker

- Actually, Docker uses the volume driver plugins to manage the volumes.
- We can use the following command to list the volume driver plugins:

```bash
docker volume ls
```
- Depending upon the requirement, we can use the volume driver plugins to manage the volumes.

### Container Storage Interface (CSI)

- Container Storage Interface (CSI) is a standard for exposing arbitrary block and file storage systems to containerized workloads on Container Orchestration Systems like Kubernetes.
- It is a standard that is implemented by the storage vendors to provide the storage to the containerized workloads.

Date of Commit: 12/03/2024