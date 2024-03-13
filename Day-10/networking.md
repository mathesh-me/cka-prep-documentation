## Networking

### Switching:

- Switching is used to connect two or more servers in a network. It is a process of receiving data from one network device and sending it to the destination device. It is a process of forwarding data frames from source to destination.
- We can connect two devices by connect thier network interfaces to the switch.

#### Common Commands:

- List the network interfaces:
```bash
ip link
```
- List the IP address of the network interfaces:
```bash
ip addr
```

- Add IP address to the network interface:
```bash
ip addr add 192.168.2.0/24 dev eth0
```

### Routing:

- Switching is used only in the single network. If we want to connect two different networks, then we have to use routing.
- We have to connect switches in different networks to the router. So that the router can route the data from one network to another network.

#### Common Commands:

- Check the routing table:
```bash
route or ip route
```

- Add the route to the routing table:
```bash
ip route add Destination_Network(192.168.2.0/24) via Gateway(192.168.2.1)
```
- For unknown destination, the router will send the data to the default gateway.
```bash
ip route add default via Gateway(192.168.2.1)
```

### Using Host as a Router:

- If Host A interface is connected with Host B interface and Host B interface is connected with Host C Interface, then we can use Host B as a router to route the data from Host A to Host C.
- We need to add the route entry in the routing table of Host A to route the data to Host C via Host B.
- We also have to enable the IP forwarding by using the following command:
```bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Date of Commit: 12/03/2024