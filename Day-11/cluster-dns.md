## Cluster DNS

- Cluster DNS is used for configuring the DNS server in our cluster.
- It is used to resolve the DNS names of the services that we deploy in our cluster.
- It is also used to resolve the DNS names of the pods that we deploy in our cluster.
- When we create a service, a DNS name will be created for the service.
The DNS name will be in the following format:
```
<service-name>.<namespace-name>.svc.cluster.local
```
- For Pods,
The DNS name will be in the following format:
```
<pod-name>.<namespace-name>.pod.cluster.local
```
- But the different here is Pods name will be in format of ip address separated by hyphens instead of dots.

Date of Commit: 13/03/2024