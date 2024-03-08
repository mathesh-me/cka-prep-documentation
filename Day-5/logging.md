## Logging in Kubernetes

- Logging is a crucial part of any application. It helps in debugging, monitoring, and troubleshooting the application.

### Commands to check the logs of a pod

- To check the logs of a pod, we can use the following command:
```bash
kubectl logs -f <pod-name>
```

- To check the logs of a pod with multiple containers, we can use the following command:
```bash
kubectl logs -f <pod-name> -c <container-name>
```

Date of Commit: 07/03/2024