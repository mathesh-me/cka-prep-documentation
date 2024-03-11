## API Groups

- API groups make it easier to extend the Kubernetes API. The API group is specified in a REST path and in the apiVersion field of a serialized object.
- There are several API groups in Kubernetes:
    - The core (also called legacy) group is found at REST path /api/v1. The core group is not specified as part of the apiVersion field, for example, apiVersion: v1.
    - The named groups are at REST path /apis/$GROUP_NAME/$VERSION and use apiVersion: $GROUP_NAME/$VERSION (for example, apiVersion: batch/v1). You can find the full list of supported API groups in Kubernetes API reference.
    - There are many other api groups are there like version, healthz, metrics and logs etc.
- For Example `curl https://kube-master:6443/version` will return kubernets version, `curl https://kube-master:6443/api/v1/pods` will return all the pods in the cluster.


Date of Commit: 11/03/2024