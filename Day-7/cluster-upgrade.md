## K8S Cluster Update:

### Customization in Master node Components:

- We can also customize versions of the master node components like `kube-apiserver`, `kube-controller-manager`, `kube-scheduler`, `kubelet`, `kube-proxy`.
- The **kube-apiserver** version should be higher than all the other components. Let's take this Version as V.
- Then the **kube-controller-manager** and **kube-scheduler** versions should be V or V-1.
- Finally, the **kubelet** and **kube-proxy** versions can be V, V-1 or V-2.
- And one more thing the **kubelet** version can be V+1 or V-1.

### Upgrading the Cluster:

- We cannot upgrade the cluster directly to the latest version.
- We need to upgrade the cluster to the next version first and then to the latest version.
- For example, if the current version is `1.20.4`, we need to upgrade to `1.21.0` first and then to the `1.22.0`.

### Cluster Upgrading Methods:

- Depends on the cluster setup, we can upgrade the cluster in different ways.
- For managed clusters like GKE, EKS, AKS, the cloud provider will take care of the upgrade.
- For self-managed clusters, we need to upgrade the cluster manually.
- For kubeadm clusters, we can use the `kubeadm upgrade plan` and  `kubeadm upgrade apply` and  command to upgrade the cluster.

### Cluster Upgrading Strategies:

- We have to update the master nodes first and then the worker nodes.
- For worker nodes we have three strategies:
    - **All at once:** We can upgrade all the worker nodes at once.
    - **One by one:** We can upgrade one worker node at a time.
    - **Adding new VMs:** We can add new VMs with the new version and then remove the old VMs.

To upgrade the cluster fully, Refer the official documentation: [Kubernetes Cluster Upgrade](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/)

Date of Commit: 09/03/2024