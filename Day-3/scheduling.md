## Scheduling in Kubernetes

### Manual Scheduling

- Kubernetes supports manual scheduling of pods.
- You can schedule a pod to a specific node using nodeName field in the pod definition file.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
spec:
    nodeName: node01
    containers:
    - name: myapp-container
        image: nginx
```

- If the nodeName field is not specified, then the pod will be scheduled to a node based on the default scheduling algorithm.
- If the nodeName specified in the pod definition file does not exist, then the pod will remain in the pending state.
- By default this changes will only apply to the next scheduling of the pod. If you want to apply this change to the existing pod, then you need to delete the pod and recreate it.
- To specify node for existing pod, We have to create a binding object and then send post request to the pod binding API server.
- Binding object is defined in the below syntax:

```yaml
apiVersion: v1
kind: Binding
metadata:
  name: myapp-pod
target:
  apiVersion: v1
  kind: Node
  name: node01
```
- While sending the request we have to convert the binding object from yaml to json format.

Date of Commit: 05/03/2024
