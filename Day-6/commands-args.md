## Commands and Args in Kubernetes

### Docker Method:

- In Docker, we can specify the command and arguments in the Dockerfile using the `CMD` and `ENTRYPOINT` instructions.
- **Entrypoint** is the command that is executed when the container starts. It will not be overridden by the command line arguments.
- **CMD** is the default command that is executed when the container starts. It can be overridden by the command line arguments.
- Sample Dockerfile:
  ```Dockerfile
  FROM ubuntu
  ENTRYPOINT ["sleep"]
  CMD ["10"]
  ```
- When we run `docker run <image-name>`, it will execute the `sleep 10` command.
- If we run `docker run <image-name> 20`, it will execute the `sleep 20` command.
- To override the `ENTRYPOINT` command, we can use the `--entrypoint` flag.
```
docker run --entrypoint sleep2.0 <image-name> 20
```
- The above command will execute the `sleep2.0 20` command.

### Kubernetes Method:

- In Kubernetes, we can specify the command and arguments in the pod definition file.
- We can specify the command and arguments in the `spec` section of the pod definition file.
- Sample Pod Definition File:
  ```yaml
  apiVersion: v1
  kind: Pod
  metadata:
    name: command-demo
  spec:
    containers:
    - name: command-demo-container
      image: ubuntu
      command: ["sleep"]
      args: ["10"]
  ```
- In Kubernetes, the `command` will override the `ENTRYPOINT` of the Docker image Dockerfile.
- The `args` will override the `CMD` of the Docker image Dockerfile.

Date of Commit: 08/03/2024