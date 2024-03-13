## Container Network Interface (CNI)

- Normally All container runtimes follow the same approach to connect the containers to the network.
- Instead of every runtimes using their individual approach to connect the containers to the network, We can use the standard approach to connect the containers to the network.
- Because most of the approaches are similar to each other. And there is only a little difference between the approaches.
- We can combine all the approaches to make a single program or script  to connect the containers to the network.
- So that we just release the burden of container runtimes. We can simplify it like by just using command like `bridge add 2e34dcf34 /var/run/netns/2e34dcf34` to establish the connection between the container and the network.


#### CNI plugins

- So the abobve ideas leads to the creation of CNI plugins.
- Any one can create the CNI plugins. That plugin must have the following features:
    - Must support command line arguments ADD/DEL/CHECK
    - Must support parameters container id, network ns etc..
    - Must manage IP Address assignment to PODs
    - Must Return results in a specific format
- The Container runtimes also have to follow some rules to use the CNI plugins.
    - Container Runtime must create network namespace
    - Identify network the container must attach to
    - Container Runtime to invoke Network Plugin (bridge) when container is ADDed.
    - Container Runtime to invoke Network Plugin (bridge) when container is DELeted.
    - JSON format of the Network Configuration

#### Problems with the CNI in Docker

- Docker doesn't use CNI plugins. It uses CNM.
- CNM is also a standard for connecting the containers to the network.
- But that doesn't mean that we cannot use CNI plugins with Docker.
- We have first launch the container with no network and then we can use the CNI plugins to connect the container to the network.
- Like below:
```bash
docker run --network=none nginx
bridge add 2e34dcf34 /var/run/netns/2e34dcf34
```

Date of Commit: 12/03/2024