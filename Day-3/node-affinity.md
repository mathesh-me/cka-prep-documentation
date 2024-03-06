## Node Affinity

Node affinity is a set of rules used by the scheduler to determine where a pod can be placed. It allows you to constrain which nodes your pod is eligible to be scheduled based on labels on the node.

### Node Affinity Definition

- Node affinity is defined in the pod definition file.
- Use the below syntax to define node affinity in a pod definition file:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
spec:
    containers:
    - name: myapp-container
        image: nginx
    affinity:
        nodeAffinity:
            requiredDuringSchedulingIgnoredDuringExecution:
                nodeSelectorTerms:
                - matchExpressions:
                - key: size
                    operator: In
                    values:
                    - Large
                    - Medium
```

- The above node affinity will ensure that the pod is scheduled on a node with the label size=Large or size=Medium.
- **Node Affinity Types:**
  - **requiredDuringSchedulingIgnoredDuringExecution:** If the rules are not met, the pod will not be scheduled.
  - **preferredDuringSchedulingIgnoredDuringExecution:** If the rules are not met, the pod will still be scheduled, but the scheduler will try to prioritize the nodes that match the rules.

You can set many other rules using node affinity. Refer to the official Kubernetes documentation: [Node Affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#node-affinity)

Date of Commit: 05/03/2024