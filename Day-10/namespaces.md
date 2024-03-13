## Namespace in Linux

- A namespace wraps a global system resource in an abstraction that makes it appear to the processes within the namespace that they have their own isolated instance of the global resource.

### Commands to create namespace:
    
- To create a namespace, we can use the following command:
```
ip netns add namespace_name
```
- To list the namespaces, we can use the following command:
```
ip netns list
```

- To `exec` into the namespace, we can use the following command:
```
ip netns exec namespace_name command or ip -n namespace_name link 
```

- To add the network interface to the namespace, we can use the following command:
```bash
ip link add veth-name_1 type veth peer name veth-name_2
ip link set veth-interface_name netns interface_name # To set
ip addr add 192.168.15.1 dev veth-ns_name # To add the IP address
```
- The above command will add the network interface to the namespace.


### Linux Bridge

- We can use Linx bridge to connect multiple namespaces together.
- To create a bridge, we can use the following command:
```bash
ip link add br0 type bridge
ip link set dev v-net-0 up
```
- Let's consider a scenario like we already done the connection betwen the namespace and the bridge. Now we can access the namespace from the host using the bridge. And my host network has connection to some other network. And I also updated my namepace route table to route to another network.
- But what If I ping from one of my namespace to another network, it will not give any error but it will also not give any ouput.
- This is because the another network does not know about the namespace IP address.
- In this case we can use NAT to connect the namespace to the network.
- Use the below command to enable NAT routing:
```bash
iptables -t nat -A POSTROUTING -s 192.168.15.0/24 -j MASQUERADE
```
- This above command will mask the IP address of the namespace to the it's own Ip address. So it will receive response in its Ip and the namespace will be able to connect to the network.


### Application Hosting in Namespace using NAT

- Let's say our application is running in the namespace on port 80 and we want users form outside to access our network.
- We can use NAT to connect the namespace to the host network. And then we can use the host network to connect to the outside network.
- Use the below command to enable NAT routing:
```bash
iptables -t nat -A PREROUTING --dport 80 --to-destination 192.168.15.2:80 -j DNAT
```

Date of Commit: 12/03/2024