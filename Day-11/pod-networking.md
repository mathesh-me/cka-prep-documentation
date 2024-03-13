## Pod Networking

### Pod Networking:

- Each pod has its own IP address.
- Each pod can communicate with other pods in the same node.
- Each pod can communicate with other pods in the different nodes.

### Pod Networking Solutions:

- To make the solution for above Pod Netwoking, We have to run the following commands on the nodes.

```bash
ip link add name br0 type bridge # Create a bridge
ip link set br0 up # Enable the bridge
ip addr add ip_addr/24 dev br0 # Add IP address to the bridge
ip link add veth-red type veth peer name veth-red-br # Create a veth pair
ip link set veth-red netns red # Move one end of the veth pair to the red namespace
ip -n red addr add ip_addr dev veth-red # Add IP address to the veth pair
ip -n red link set veth-red up # Enable the veth pair
ip link set veth-red-br master br0 # Add the veth pair to the bridge
ip netns exec blue ip route add Dest_addr via bridge_addr # Add the route to the routing table
iptables iptables -t nat -A POSTROUTING -s ip_addr -j MASQUERADE # Enable the NAT
```
- By running the above commands, we can make the pod networking solution.
- We have to run the above commands on all the nodes.
- Instead of running the above commands individually on all the nodes, we can make a script and run the script on all the nodes.
- Bridge: It is like a switch. It is used to connect two or more network interfaces. So all pods on each nodes connect to the bridge on each node. And then by the brigde, all pods can communicate with each other.
- If we have only few number of nodes, we can add route manually from one pod to another. But if we have large number of nodes, then we can have to use some centralized router to route the data from one node to another node.

### CNI (Container Network Interface):

#### CNI Plugins:

- Already we created one sript to make the pod networking solution. CNI plugins are also like a script But it also include some commands like DEL) ands ADD) to add and delete the network interfaces. So whenever a pod is created, the CNI plugin will be called to add the network interface to the pod. And whenever a pod is deleted, the CNI plugin will be called to delete the network interface from the pod.
- This CNI plugins are invoked by the kubelet to add and delete the network interfaces to the pods.
- If we look into kubelet configuration file, we can see the CNI plugin path. By default, the CNI plugin path is /opt/cni/bin. So whenever a pod is created, the kubelet will call the CNI plugin to add the network interface to the pod. And whenever a pod is deleted, the kubelet will call the CNI plugin to delete the network interface from the pod.
- `--cni-conf-dir=/etc/cni/net.d` is the default path for the CNI configuration file. It also will be added in kubelet configuration file.
- Finally kubelet will run some command like `./net-script.sh add <container> <namespace>` to add the network interface to the pod. And `./net-script.sh del <container> <namespace>` to delete the network interface from the pod.

#### CNI File location in kubelet:

- `--network-plugin=cni` is the default network plugin in kubelet configuration file.
- `--cni-conf-dir=/etc/cni/net.d` is the default path for the CNI configuration file in kubelet configuration file.
- `--cni-bin-dir=/opt/cni/bin` is the default path for the CNI plugin in kubelet configuration file.
- If we use `ls /etc/cni/net.d`, we can see the CNI configuration file. And the plugin will be used.
- If we use `ls /opt/cni/bin`, we can see all the available CNI plugins in our cluster.
- We can use `cat /etc/cni/net.d/plugin.conf` to see the configuration of the plugin.


Date of Commit: 13/03/2024