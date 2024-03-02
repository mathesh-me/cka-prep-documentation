## Replication Controller and Replica Set

- **Replication Controller** is the older version of Replica Set. It is used to ensure that a specified number of pod replicas are running at any given time. 
- **Replica Set** is the newer version of Replication Controller. It is also doing same work as Replication Contoller but with more advanced version of Replication Controller.

### Use Cases

- Let's say I have a pod running in my K8S cluster. And I want to ensure that there are always 3 replicas of that pod running in my K8S cluster. So, I can use Replication Controller or Replica Set to ensure that there are always 3 replicas of that pod running in my K8S cluster.

### Replication Controller and Replica Set Difference

- Replication Controller Definition File
```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: myapp-rc
spec:
    replicas: 3
    template:
        metadata:
        name: myapp-pod
        labels:
            app: myapp
        spec:
        containers:
        - name: myapp-container
            image: nginx
```
    
- Replica Set Definition File
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-rs
spec:
    replicas: 3
    selector:
        matchLabels:
        app: myapp
    template:
        metadata:
        name: myapp-pod
        labels:
            app: myapp
        spec:
        containers:
        - name: myapp-container
            image: nginx
```

- The only difference between Replication Controller and Replica Set is that in Replica Set we have a selector field. Selector field is used to select the pods that we want to manage. In Replication Controller, we don't have a selector field.

Commit Date: 02/03/2024
