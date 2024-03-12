### Image Security

- For using our Private Repository images, We need to create a secret with type `docker-registry`.
- We can create the secret using the following command:
  
```bash
kubectl create secret docker-registry myregistrykey --docker-server=DOCKER_REGISTRY_SERVER --docker-username=DOCKER_USER --docker-password=DOCKER_PASSWORD --docker-email=DOCKER_EMAIL
```
  - `myregistrykey` is the name of the secret.
  - `DOCKER_REGISTRY_SERVER` is the URL of the Docker Registry.
  - `DOCKER_USER` is the username of the Docker Registry.
  - `DOCKER_PASSWORD` is the password of the Docker Registry.
  - `DOCKER_EMAIL` is the email of the Docker Registry.

- We can use the secret in the pod definition file as follows:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: private-reg
spec:
  containers:
  - name: private-reg-container
    image: DOCKER_REGISTRY_SERVER/IMAGE_NAME:TAG
  imagePullSecrets:
  - name: myregistrykey
```

Date of Commit: 11/03/2024