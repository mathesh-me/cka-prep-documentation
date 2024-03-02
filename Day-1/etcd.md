## ETCD

- **etcd** is a distributed key-value store that provides a reliable way to store data across a cluster of machines.

### ETCD in Kubernetes

- **etcd** is used as a data store for the Kubernetes cluster. It stores the configuration data of the cluster and represents the overall state of the cluster at any given point in time.
- When you create a pod, service, or deployment, the data is stored in etcd. When you update the configuration of a pod, service, or deployment, the data is updated in etcd. When you delete a pod, service, or deployment, the data is deleted from etcd.

### Install etcd

- Install binaries from the below link:
```
https://github.com/etcd-io/etcd/releases/download/v3.3.11/etcd-v3.3.11-linux-amd64.tar.gz
```
- Extract the binaries and move them to the `/usr/local/bin` directory.
```
tar -xvf etcd-v3.3.11-linux-amd64.tar.gz
mv etcd-v3.3.11-linux-amd64/etcd* /usr/local/bin/
```
- Run the below command to check the version of etcd.
```
etcd --version
```

### Additional Information on etcd

- ETCDCTL is the CLI tool used to interact with ETCD.
- ETCDCTL can interact with ETCD Server using 2 API versions - Version 2 and Version 3.  By default its set to use Version 2. Each version has different sets of commands.

- For example ETCDCTL version 2 supports the following commands:

etcdctl backup<br>
etcdctl cluster-health<br>
etcdctl mk<br>
etcdctl mkdir<br>
etcdctl set<br>

- Whereas the commands are different in version 3

etcdctl snapshot save<br>
etcdctl endpoint health<br>
etcdctl get<br>
etcdctl put<br>

- To set the right version of API set the environment variable ETCDCTL_API command `export ETCDCTL_API=3`
- When API version is not set, it is assumed to be set to version 2. And version 3 commands listed above don't work. When API version is set to version 3, version 2 commands listed above don't work.
- Apart from that, you must also specify path to certificate files so that ETCDCTL can authenticate to the ETCD API Server. The certificate files are available in the etcd-master at the following path. We discuss more about certificates in the security section of this course. So don't worry if this looks complex:

```
--cacert /etc/kubernetes/pki/etcd/ca.crt     
--cert /etc/kubernetes/pki/etcd/server.crt     
--key /etc/kubernetes/pki/etcd/server.key

```
So for the commands to work you must specify the ETCDCTL API version and path to certificate files. Below is the final form:
```
kubectl exec etcd-master -n kube-system -- sh -c "ETCDCTL_API=3 etcdctl get / --prefix --keys-only --limit=10 --cacert /etc/kubernetes/pki/etcd/ca.crt --cert /etc/kubernetes/pki/etcd/server.crt  --key /etc/kubernetes/pki/etcd/server.key"
```

Commit Date: 02/03/2024