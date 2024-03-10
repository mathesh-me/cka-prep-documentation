## TLS in Kubernetes

- TLS certificates are used to secure the communication between the Kubernetes components and the communication between the client and the server.

### TLS Certificates

- The Keys associated with servers are called Server certificates.
- The keys associated with clients are called Client certificates.
- The Keys associated with the Certificate Authority are called Root certificates.

### Servers and Clients in Kubernetes

- In kubernetes, the `kube-apiserver`, `etcd` and `kubelet` are servers.
- Human administrators, developers, `kube-scheduler`, `kube-controller-manager` and `kube-proxy` are clients.
- We have to create the server certificates for the servers and client certificates for the clients.
- But if we consider from `etcd` the `kube-apiserver` is a also a client. We can use the same keys(kube-api-sever keys) or we can also create a new one.
- As well as `kubelet` and `kube-api server` are clients to each other. We can use the same keys(their server keys) for `kube-api-server` and `kubelet` also or we can also create a new one(clinet keys for `kubelet` and server keys for `kube-api-server).

Date of Commit: 10/04/2024