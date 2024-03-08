## Init Containers

- Init Containers are containers that run before the main container in a Pod.
- They can contain utilities or setup scripts not present in the main container.
- They are useful when the main container depends on some pre-requisites to be present before it starts.
- Init Containers are defined in the Pod definition file, just like the main container.

### Creating Init Containers in a Pod

- We can define multiple init containers in a Pod definition file.
- The below example shows how to define init containers in a Pod definition file:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: init-container-pod
spec:
  containers:
  - name: main-container
    image: busybox
    command: ['sh', '-c', 'echo The application is running! && sleep 3600']
  initContainers:
  - name: init-container1
    image: busybox
    command: ['sh', '-c', 'echo Init Container 1']
  - name: init-container2
    image: busybox
    command: ['sh', '-c', 'echo Init Container 2']
```

Date of Commit: 08/03/2024