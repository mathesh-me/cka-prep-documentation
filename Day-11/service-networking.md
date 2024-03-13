## Service Networking

- We already know that Pod networking.
- Service networking is different from pod networking. The Service we deploy will be available to all nodes in the cluster.
- The service will have a virtual IP address.
- It is not like any server or service exists in the cluster. It is just a virtual service with a virtual IP address.
- kube-proxy will be running on all the nodes. It will be responsible for the service networking.
- kube-proxy will create the iptables rules to forward the traffic to the service for every service that we deploy.
- There are three types of options to forward the traffic to the service:
  - Userspace
  - Iptables
  - IPVS
- By default, kube-proxy will use the iptables to forward the traffic to the service. We can use kube-proxy logs to see what option it is using.


### Service IP Address:

- We can see the service Ip range in api-server in --service-cluster-ip-range option.
- The Only constraint is that the service IP range should not overlap with the pod IP range.

Date of Commit: 13/03/2024