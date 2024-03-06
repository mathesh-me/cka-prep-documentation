## Daemon Sets

Daemon Sets are used to ensure that some or all nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. As nodes are removed from the cluster, those Pods are garbage collected. Deleting a DaemonSet will clean up the Pods it created.

### Daemon Set Definition

- Daemon Sets are defined in the DaemonSet definition file.
- Use the below syntax to define a Daemon Set in a DaemonSet definition file:

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: myapp-ds
spec:
    selector:
        matchLabels:
        app: myapp
    template:
        metadata:
        name: myapp-pod
        labels:
            app: myapp
        spec:
        containers:
        - name: myapp-container
            image: nginx
```

- The above Daemon Set will ensure that a copy of the Pod is running on all nodes with the label app=myapp.

### Use Cases

- running a cluster storage daemon on every node
- running a logs collection daemon on every node
- running a node monitoring daemon on every node

### Daemon Set Commands

- To create a Daemon Set, use the below command:

```bash
kubectl create -f myapp-ds.yaml
```

- To get the list of all Daemon Sets, use the below command:

```bash
kubectl get daemonsets
```

- To get the details of a specific Daemon Set, use the below command:

```bash
kubectl describe daemonset myapp-ds
```

- To delete a Daemon Set, use the below command:

```bash
kubectl delete daemonset myapp-ds
```

You can set many other rules using Daemon Sets. Refer to the official Kubernetes documentation: [Daemon Sets](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)

Date of Commit: 06/03/2024