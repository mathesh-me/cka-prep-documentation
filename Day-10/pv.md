## Persistent Volume

- In Kubernetes, the persistent volume is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes.

### Creating Persistent Volume

- We can create the persistent volume by using the following yaml file:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-volume
spec:
    capacity:
        storage: 1Gi
    accessModes:
        - ReadWriteOnce
    persistentVolumeReclaimPolicy: Retain
    hostPath:
        path: "/mnt/data"
```

Date of Commit: 12/03/2024