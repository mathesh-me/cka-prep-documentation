## Namespaces in Kubernetes

- Namespaces are a way to divide cluster resources between multiple users or environments.
- Let's say we have a K8S cluster and we want to divide the resources of that K8S cluster between environments. Because we don't wants to allow one environement to see the resources of another environment. So, we can use namespaces to divide the resources of that K8S cluster between environments.
- We can also use namespaces to divide the resources of that K8S cluster between multiple environments. So that a environment we can allocate a specific amount of resources to a one environment and a specific amount of resources to another environment.

### Namespace Definition File

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: my-namespace
```

### kubectl namespace commands

- **Create Namespace**: `kubectl create -f namespace-definition-file.yaml`
- **Get Namespaces**: `kubectl get namespaces`
- **Get Pods in a Namespace**: `kubectl get pods -n my-namespace`
- **Get All Resources in a Namespace**: `kubectl get all -n my-namespace`
- **Delete Namespace**: `kubectl delete namespace my-namespace`

Commit Date: 03/03/2024