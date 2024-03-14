## Designing Kubernetes Cluster:

- We have to design our Cluster depends upon workloads, purpose, and requirements.
- We also have to consider application traffic, kind, resource requirements etc.,

### Purpose:

- We have to ask ourself for What purpose we are designing this cluster?
- Whether it is for Education, Development, Testing, Production, or for any other purpose.
- For Example: If it for learning we can `minikube` or single node cluster with kubeadm, AKS, GKE, EKS, etc.,
- For Development, Testing we can setup multi node cluster with one master and multiple worker nodes using kubeadm or any other managed services.
- For Production, We can setup Mutli node Cluster iwth Multiple Master nodes.

### Hosting Infrastucture:

- For onprem we can use kubeadm to setup cluster.
- For Cloud, we can use managed services like AKS, GKE, EKS, etc.,

### Storage:

- For High Performance - SSD backed storage.
- Multiple Concurrent Connections - Network based Storage.
- Persistent Volumes for data shared accross pods.

### Nodes:

- We can use either physical or virtual machines.
-  X86_64 Architecture is most commonly used.

### Master Node up:

- We can have multiple master nodes for high availability.
- Also we can have for multiple etcd nodes for better performance.

### Turnkey vs Hosted Solutions:

- For Turnkey solutions we have to manage everything.
- For Hosted solutions, we can use managed services like AKS, GKE, EKS, etc.,
- Trunkey solutions examples: vagrant, openshift, cloud foundry runtimes, etc.,

### Network:

- For Networking, We can use `flannel`, `calico`, `weave`, `cilium`, etc.,

---

## HA Cluster Design:

- We can have multiple master nodes for high availability.
- So if we have multiple master nodes, we will also have multiple master node components like `kube-apiserver`, `kube-controller-manager`, `kube-scheduler`, `etcd`, etc.,
- So we also have how the master node componets works across multiple master nodes. 
- We will have to use `kube-api` for many things. so we can set `active-active` mode and deploy load balancer in front of kube-api.
- For `control-manager` and `scheduler` we can use `leader election` to elect leader and work on that leader. So we can use `active-stanby` mode.
- There are many options available for leader election like lease duration, renew duration, retry period, etc.,
- For `etcd` we can use either stacked etcd or external etcd. Stacked etcd is where etcd is running on master nodes itself. External etcd is where etcd is running on separate nodes. We just need to change the etcd servers endpoints in kube-apiserver configuration.


Date of Commit: 14/03/2024