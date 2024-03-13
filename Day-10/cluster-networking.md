## Cluster Networking

- In cluster Each node will have its own IPv4 address, own hostname and its own IPV6 address.
- The master nodes consists of various components like API server, Controller manager, Scheduler, etcd and kubelet.
- And worker nodes will have kubelet, kube-proxy.
- So Each service listens on a specific port inside the cluster.
- We need to open the ports in the firewall to allow the traffic to the services. So that all components can communicate with each other.

Refer Kuberenetes official documentation for ports information: [K8S Ports](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/#check-required-ports)

Date of Commit: 12/03/2024