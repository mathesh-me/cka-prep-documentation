## Static Pods

- Static Pods are managed directly by the kubelet daemon on a specific node, without the API server observing them. Unlike Pods that are managed by the control plane (for example, a Deployment); instead, the kubelet watches each static Pod (and restarts it if it fails).

- Static Pods are always bound to one Kubelet on a specific node.

- The kubelet automatically tries to create a mirror Pod on the Kubernetes API server for each static Pod. This means that the Pods running on a node are visible on the API server, but cannot be controlled from there. The Pod names will be suffixed with the node hostname with a leading hyphen.

### More about Static Pods

- Static Pods are managed directly by the kubelet daemon on a specific node, without the API server observing them. Unlike Pods that are managed by the control plane (for example, a Deployment); instead, the kubelet watches each static Pod (and restarts it if it fails).
- Static Pods are always bound to one Kubelet on a specific node.
- So we have to create the static pod definition file on some specific location on the node and kubelet will take care of the rest.
- We just have to mention the static pod definition file location in the kubelet configuration file.
- There is two option to mention the static pod definition file location in the kubelet configuration
    - `--pod-manifest-path` flag
    - `staticPodPath` field in the kubelet configuration file by using the `--config` flag.
- If the file is created in the location mentioned in the kubelet configuration file, then the kubelet will create the pod from the definition file.
- If the file is deleted from the location mentioned in the kubelet configuration file, then the kubelet will delete the pod.

Date of Commit: 06/03/2024