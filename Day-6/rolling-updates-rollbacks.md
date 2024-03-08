## Rolling Updates and Rollbacks

### Rolling Updates

- Normally when we create a deployment, it creates a ReplicaSet and the ReplicaSet creates the pods. And it will also add Revision History to the deployment.
- When we update the deployment, it will create a new ReplicaSet and the new ReplicaSet will create the new pods with the updated image. And the Revision History will be updated with the new revision.
- Every time we update the deployment, it will create a new ReplicaSet and the new ReplicaSet will create the new pods with the updated image. And the old ReplicaSet will delete the old pods.


### Deployment Strategy:

- **Recreate** - It will kill all the old pods and create new pods with the updated image. There will be a Downtime in this strategy.
- **RollingUpdate** - It will create new pods with the updated image and then kill the old pods one by one. This is the default strategy.

### Rollout Commands:

- To check the rollout status, we can use the following command:
```bash
kubectl rollout status deployment <deployment-name>
```

- To check the rollout history, we can use the following command:
```bash
kubectl rollout history deployment <deployment-name>
```

- To rollback to the previous version, we can use the following command:
```bash
kubectl rollout undo deployment <deployment-name>
```

Date of Commit: 08/03/2024

