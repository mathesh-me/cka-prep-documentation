## K8S Secrets

- Kubernetes Secrets let you store and manage sensitive information, such as passwords, OAuth tokens, and ssh keys. Storing confidential information in a Secret is safer and more flexible than putting it as a plain text in a Pod definition or in a container image.
- Creation of a Secret is similar to that of a ConfigMap. But we have to store the sensitive data in base64 encoded format.
- We can use a Secret as environment variables, as a file in a volume, or as a command-line argument to a container.

### Create a Secret

- We can create a Secret using the `kubectl create secret` command.
- Use the below command to create a Secret from a literal value:   
```shell
kubectl create secret generic <secret-name> --from-literal=<key>=<value>
```

- Use the below command to create a Secret from a file:
```shell
kubectl create secret generic <secret-name> --from-file=<path-to-file>
```

- Using Definition file:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: <secret-name>
type: Opaque
data:
  <key>: <base64-encoded-value>
```

### View a Secret

- Use the below command to view a Secret:
```shell
kubectl get secrets
```

### View the details of a Secret

- Use the below command to view the details of a Secret, But it will not show the actual data:
```shell
kubectl describe secret <secret-name
```

- To view the actual data, use the below command:
```shell
kubectl get secret <secret-name> -o yaml
```

**Using a Secret as environment variables**

- It is similar to using a ConfigMap as environment variables.
- Refer ConfigMap section for more details.

Date of Commit: 08/03/2024

