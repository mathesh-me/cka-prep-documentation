## Multi Containers in a Pod

- For some reason, we might want to run multiple containers in a single Pod. For example, we might want to run a sidecar container that adds some functionality like logging or monitoring to the main container.

### Behaviour of Multi Containers in a Pod

- All containers in a Pod share the same network namespace, so they can communicate with each other using localhost.
- If one of the containers in a Pod fails, Kubernetes restarts the Pod and all of its containers.
- All containers in a Pod are scheduled on the same node, and they share the same resources, such as storage and CPU.
- They are deployed and scaled together as a single unit.

### Creating Multi Containers in a Pod

- We can define multiple containers in a Pod definition file.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: multi-container-pod
spec:
  containers:
  - name: container1
    image: nginx
  - name: container2
    image: busybox
    command: ['sh', '-c', 'echo Hello from the second container']
```

Date of Commit: 08/03/2024