## Trouble Shooting

### Application Troubleshooting

- Make a outline of your application Architecture.
- Check all the objects one by one.
- Use `kubectl describe pod pod_name` to check the status of the objects.
- Use `kubectl logs pod_name` to check the logs of the pods.

### Control Plane Troubleshooting

- Check the status of the control plane components.
- Use `kubectl get nodes` to check the status of the nodes.
- Use `kubectl get pods -n kube-system` to check the status of the control plane components.
- Check the status of every service individually using `service service_name status`.
- If your Components are deployed using `kubeadm`, use `kubectl logs pod_name -n kube-system` to check the logs of the control plane components.
- If your Components are deployed using `kubeadm`, use `journalctl -u kubelet` to check the logs of the kubelet service.

### Worker Node Troubleshooting

- Use `kubectl get nodes` to check the status of the nodes.
- Use `kubectl describe node node_name` to check the status of the nodes.
- Check the status of the kubelet service using `service kubelet status`.
- Use `journalctl -u kubelet` to check the logs of the kubelet service.
- Check whether the certs are expired or not using `kubectl get csr`.
- We also need to check for `kube-proxy` the same above steps.

### Network Troubleshooting

- Check the Network Plugins related things.
- Then Check for DNS Server issues.
- Also try to check on `kube-proxy` related things.

Kubernetes Troubleshooting Docs: 
- [Troubleshooting Clusters](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/)
- [Debug Service issue](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-service/)
- [DNS Troubleshooting](https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/)


Date of Commit: 14/03/2024