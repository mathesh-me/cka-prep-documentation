## Authorization in K8S

- Authorization is the process of verifying what a user or service is allowed to do.

### Types of Authorization:

- RBAC
- Node Authorization
- Webhook Mode
- ABAC

### Node Authorization:

- If we add a component to system:node group. It will get all the permissions of the system:node group
- Example: Adding kubelet to system:node group, Because kubelet need some access to the API server to schedule the pods and to get the pod details.
- system:node permissions:
    - Read Services, Endpoints, Nodes, Pods
    - Write Node status, Pod status, events

### ABAC:

- It involves attach Policy to user sor groups directly.
- It is not recommended to use ABAC because it is deprecated.
- Policy will be in the form of JSON file.

### RBAC:

- It involves creating roles and rolebindings.
- And attach the roles to the users or groups.

### Webhook Mode:

- It is like getting the authorization from external service. Checking the user permissions from external service.
- Example: Open Policy Agent(OPA)

### View Authorization Modes:

- we can see the authorization modes in kube-apiserver.yaml file.

```yaml
- --authorization-mode=Node,RBAC,Webhook,ABAC
```
- The authorization modes are in the form of priority. If the first mode fails, then it will go to the next mode.

### Other Authorization Modes:

- AlwaysDeny: It will deny all the requests.
- AlwaysAllow: It will allow all the requests.

Date of Commit: 11/03/2024