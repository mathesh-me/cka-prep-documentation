## API Groups

- API groups make it easier to extend the Kubernetes API. The API group is specified in a REST path and in the apiVersion field of a serialized object.
- There are several API groups in Kubernetes:
    - The core (also called legacy) group is found at REST path /api/v1. The core group is not specified as part of the apiVersion field, for example, apiVersion: v1.
    - The named groups are at REST path /apis/$GROUP_NAME/$VERSION and use apiVersion: $GROUP_NAME/$VERSION (for example, apiVersion: batch/v1). You can find the full list of supported API groups in Kubernetes API reference.
    - There are many other api groups are there like version, healthz, metrics and logs etc.
- For Example `curl https://kube-master:6443/version` will return kubernets version, `curl https://kube-master:6443/api/v1/pods` will return all the pods in the cluster.

### Listing API Groups

- We can list the API groups by running the following command:
```bash
curl -k https://kube-master:6443 or curl -k https://kube-master:6443/apis
```
- We can also list the API groups by running the following command:
```bash
kubectl api-resources
```
- But remember when we use `curl` command, We also need to specify out key, cert and ca file.
- To avoid this we can use `kubectl-proxy` command.
- `kubectl-proxy` command will create a proxy server. It will listen on port 8001. And it will forward the request to the kube-apiserver.
- So instead of using `curl https://kube-master:6443`, we can use `curl http://localhost:8001`. So the request will be forwarded to the kube-apiserver.

Date of Commit: 11/03/2024