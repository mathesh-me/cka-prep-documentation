## Secure Hosts in Kubernetes

### Secure Hosts

- In a Kubernetes cluster, the security of the hosts is important.
- The hosts are the machines where the Kubernetes components are running.
- The security of the hosts is important because if the hosts are compromised, the whole cluster will be compromised.
- We can secure the hosts by following some best practices.
- One is we can disable the normal username and password login and use the SSH keys for login.

### Two ways involved in Security

- **Authentication:** It is the process of verifying the identity of the user.
- **Authorization:** It is the process of verifying the user has the permission to access the resources.

#### Authentication

- Files – Username and Passwords
- Files – Username and Tokens
- Certificates
- External Authentication providers - LDAP
- Service Accounts

#### Authorization

- RBAC
- ABAC
- Webhook
- Node Authorization

### TLS Certificates

- All the communication between the Kubernetes components should be secure using TLS.

### Network Policies

- We can use the network policies to control the traffic between the applications running in the cluster.

Date of Commit: 10/04/2024