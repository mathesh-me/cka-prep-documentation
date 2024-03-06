## Taints and Tolerations

### Taints

- Taints allow a node to repel a set of pods.
- Taints are set on nodes.
- Taints are key-value pairs.
- Taints have three components:
  - Key
  - Value
  - Effect
- Taint Effect:
    - NoSchedule: New pods will not be scheduled on the node.
    - PreferNoSchedule: New pods will try to avoid the node, but it is not guaranteed.
    - NoExecute: If a pod is already running on the node, then it will be evicted.
- Use the below command to add a taint to a node:
```bash
kubectl taint nodes node01 key1=value1:taint-effect
```
- Use the below command to remove a taint from a node:
```bash
kubectl taint nodes node01 key1:taint-effect-
```
- Use the below command to list all the taints on a node:
```bash
    kubectl describe node node01 | grep Taints
```

### Tolerations

- Tolerations allow a pod to be scheduled on a node with a matching taint.
- Tolerations are set on pods.
- Tolerations are key-value pairs.
- Tolerations have three components:
  - Key
  - Value
  - Effect
- Tolerations are added to the pod definition file.
- Use the below syntax to add a toleration to a pod definition file:
  ```yaml
  spec:
    containers:
    - name: myapp-container
      image: nginx
    tolerations:
    - key: "key1"
      operator: "Equal"
      value: "value1"
      effect: "NoSchedule"
  ```
- The above toleration will allow the pod to be scheduled on a node with a taint key1=value1:NoSchedule.
- If a pod has multiple tolerations, then the pod will be scheduled on a node with any of the matching taints.

Date of Commit: 05/03/2024