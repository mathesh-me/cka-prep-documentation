## ETCD in HA

- ETCD is a distributed key-value store that provides a reliable way to store data across a cluster of machines.
- Distributed means all the concurrent requests are handled by multiple `etcd` nodes.
- Which means we can read from any nodes and write to any nodes.
- But the write is different here, We cannot write to nay node. We have to write to the leader node.
- Within the nodes they will elect a leader and all the write requests are handled by the leader. And the leader is responsible for replicating the data to all the followers.
- Uses `Raft` consensus algorithm to elect a leader.
- The write operation is only successful if the all the worker nodes send response to the leader node. If one worker node fails to send response, the write operation is failed for cluster that have <=2 nodes.
- If the leader goes down, the followers will elect a new leader.

### Fault Tolerance:
- For ETCD to work in HA, we need to have odd number of nodes. Because if we have even number of nodes, the cluster will not be able to elect a leader. So it is recommended to have 3, 5, 7, etc., nodes. It is based on formula `n/2+1`.
- If we have 3 nodes, the cluster can tolerate 1 node failure. You can also have 4 node but think about the fault tolerance formula `n/2+1`. It also tolerates 1 node failure. So it is better to have 3 nodes because it also can tolerate 1 node failure.
- If we have 5 nodes, the cluster can tolerate 2 node failures. Like that goes on.

### Installation:

- Use the below command to install etcd on all the nodes.
```sh
wget -q --https-only \
"https://github.com/coreos/etcd/releases/download/v3.3.9/etcd-v3.3.9-linux-amd64.tar.gz"
tar -xvf etcd-v3.3.9-linux-amd64.tar.gz
mv etcd-v3.3.9-linux-amd64/etcd* /usr/local/bin/
mkdir -p /etc/etcd /var/lib/etcd
cp ca.pem kubernetes-key.pem kubernetes.pem /etc/etcd/
```
- We also need to give the peers information in the `etcd` configuration file.
```
--initial-cluster controller-0=https://${CONTROLLER0_IP}:2380,controller-1=https://${CONTROLLER1_IP}:2380,controller-2=https://${CONTROLLER2_IP}:2380
```

Date of Commit: 14/03/2024