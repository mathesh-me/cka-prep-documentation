## Persistent Volume Claim

- In Kubernetes, the persistent volume claim is a request for storage by a user.

### Creating Persistent Volume Claim

- We can create the persistent volume claim by using the following yaml file:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pv-claim
spec:
    accessModes:
        - ReadWriteOnce
    resources:
        requests:
        storage: 500Mi
```

- In the above yaml file, We are creating the persistent volume claim with the name `pv-claim` and requesting the storage of `500Mi` with the access mode `ReadWriteOnce`.
- So Kubernetes will find the persistent volume with the same access mode and the capacity of `500Mi` and bind the persistent volume to the persistent volume claim.
- If the persistent volume is not found, then the persistent volume claim will be in the pending state.

### Consuming Persistent Volume Claim in Pod

- We can consume the persistent volume claim in the pod by using the following Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pv-pod
spec:
  volumes:
  - name: pv-storage
    persistentVolumeClaim:
    claimName: pv-claim
  containers:
    - name: pv-container
    image: nginx
    ports:
    - containerPort: 80
    volumeMounts:
    - mountPath: "/usr/share/nginx/html"
      name: pv-storage
```
- If the persistent volume claim bound to any pod, we cannot delete the persistent volume claim.
- We have to delete the pod first, then we can delete the persistent volume claim.
- We have to mention Reclaim policy in the persistent volume yaml file so it will decide after pvc deletion whether the pv have to Delete or Recycle or Retain . If we don't mention the reclaim policy, then the default policy is `Delete`.
- Other options are `Retain` and `Recycle`.
- `Retain` will not delete the volume after pvc deletion. We have to manually delete the volume.
- `Recycle` will delete the volume after pvc deletion and create a new volume with the same name and same capacity.
- `Delete` will delete the volume after pvc deletion.

Example of pv.yml file with reclaim policy:

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