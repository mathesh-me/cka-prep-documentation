## Resource Requiremnts and Limits

- In Kubernetes, we can specify the resource requirements and limits for a container in a pod definition file.
- Resource requirements are used by the scheduler to find the best node for a pod.
- Resource limits are used to prevent a container from using more resources than the specified limit.

### Resource Requirements

- Resource requirements are defined in the pod definition file.
- Use the below syntax to define resource requirements in a pod definition file:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
spec:
    containers:
    - name: myapp-container
        image: nginx
        resources:
            requests:
                memory: "64Mi"
                cpu: "250m"
            limits:
                memory: "128Mi"
                cpu: "500m"
```

- The above resource requirements will ensure that the container in the pod has a request of 64Mi memory and 250m CPU, and a limit of 128Mi memory and 500m CPU.

- **Resource Requirements Types:**
  - **requests:** The minimum amount of resources required by the container.
  - **limits:** The maximum amount of resources that the container can use.

You can set many other rules using resource requirements and limits. Refer to the official Kubernetes documentation: [Resource Requirements and Limits](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)

Date of Commit: 06/03/2024