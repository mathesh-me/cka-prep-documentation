## Docker networking

- Use `docker network ls` to list the networks.
- By default `bridge` network is created when we install the docker.
- You can see the bridge interface as docker0 in the host.
- It will also create a namespace for the bridge network.
- By default, If we launch any containers it will lauch in that namespace, the containers will be connected to the bridge network.
- Docker will do all the process of connect the containers to the bridge network in behind the scenes. 
- We can access the application hosted inside the container by using the IP address of the container in our host.
- But people outside the network can't access the application hosted inside the container.
- So we have to use the port forwarding to access the application hosted inside the container from outside the network.
- We can use NAT to connect the container to the host network. And then we can use the host network to connect to the outside network.
- Use the below command to enable NAT routing:
```bash
iptables \
–t nat \
-A DOCKER \
-j DNAT \
--dport 8080 \
--to-destination 172.17.0.3:80
```
- You can view the NAT rules by using the following command:
```bash
iptables -nvL -t nat
```

Date of Commit: 12/03/2024