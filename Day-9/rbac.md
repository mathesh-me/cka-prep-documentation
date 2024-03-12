## RBAC

- RBAC stands for Role Based Access Control.
- It involves creating roles and rolebindings and attach the roles to the users or groups.

### Roles:

- Roles are used to define the permissions.
- It is a namespaced resource, Can be used to define the permissions within the namespace.
- Definition file for Role:

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  resourceNames: ["my-pod"] # If we want to restrict the access to specific pod
  verbs: ["get", "watch", "list"]
```

### RoleBinding:

- RoleBinding is used to attach the roles to the users or groups.
- Definition file for RoleBinding:

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: default
subjects:
- kind: User
  name: user1
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

### Check Access:

- To check the access, we can use the following command:

```bash
kubectl auth can-i get pods --as user1
```

- This command will return `yes` if the user has access to get the pods.

### Cluster Roles:

- ClusterRoles are used to define the permissions at the cluster level.
- Namespace is not required for ClusterRoles.
- Namespace ascoped resources are pod, service, replicationcontroller, deployment, job, etc.
- ClusterRoles are used to define the permissions for the cluster scoped resources like nodes, namespaces, persistentvolumes, persistentvolumeclaims, certificateSigningRequests, clusterrolebindings, clusterroles, etc.
- Creation of ClusterRole and ClusterRoleBinding is similar to Role and RoleBinding.
- We can use the same definition file for ClusterRole and ClusterRoleBinding, just remove the namespace from the definition file. And specify Cluster Level resources in the resources field.

Date of Commit: 11/03/2024