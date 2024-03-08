## Environment Variables in Kubernetes

### Define an environment variable for a container
- When you create a Pod, you can set environment variables for the containers that run in the Pod. To set environment variables, include the env or envFrom field in the configuration file.

- The **env** and **envFrom** fields have different effects.

    - `env` allows you to set environment variables for a container, specifying a value directly for each variable that you name.<br>
    - `envFrom` allows you to set environment variables for a container by referencing either a ConfigMap or a Secret. When you use envFrom, all the key-value pairs in the referenced ConfigMap or Secret are set as environment variables for the container. You can also specify a common prefix string.

- The following example shows how to set environment variables for a container using the env field:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - name: mycontainer
    image: redis
    env:
    - name: ENV_VAR1
      value: "value1"
    - name: ENV_VAR2
      value: "value2"
```

Date of Commit: 08/03/2024