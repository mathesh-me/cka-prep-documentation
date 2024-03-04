## Deployment

### Why Deployment?

- **Rolling Updates and Rollbacks**: Deployment allow you to update your application without downtime. You can also rollback to a previous deployment if something goes wrong.
- **Replica Sets**: Deployments create Replica Sets which are used to ensure that a specified number of pod replicas are running at any given time.
- **Scaling**: Deployments allow you to scale your application up or down.

### Deployment Definition File

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
spec:

    replicas: 3
    
    selector:
        matchLabels:
        app: myapp
    
    template:
        metadata:
        labels:
            app: myapp
        spec:
        containers:
        - name: myapp-container
            image: nginx
```

### kubectl deployment commands

- **Create Deployment**: `kubectl create -f deployment-definition-file.yaml`
- **Set Image**: `kubectl set image deployment/myapp-deployment myapp-container=nginx:1.9.1`
- **Get Deployments**: `kubectl get deployments`
- **Get Replica Sets**: `kubectl get rs`
- **Get Pods**: `kubectl get pods`
- **Rollout Status**: `kubectl rollout status deployment/myapp-deployment`
- **Rollout History**: `kubectl rollout history deployment/myapp-deployment`
- **Rollout Undo**: `kubectl rollout undo deployment/myapp-deployment`
- **Rollback**: `kubectl rollout undo deployment/myapp-deployment`

Commit Date: 03/03/2024