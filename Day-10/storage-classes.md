## Storage Classes in Kubernetes

- In Kubernetes, the storage classes are used to define the type of storage that we want to use in the cluster.
- We can use the storage classes to define the type of storage like `aws ebs`, `azure disk`, `gce persistent disk` or any other CSI supported storage.
- Storage classes allows us to have Dynamic Provisioning of the storage.

### Creating Storage Class

- We can create the storage class by using the following yaml file:

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: fast
provisioner: kubernetes.io/aws-ebs
reclaimPolicy: Retain 
parameters:
  type: gp2
  encrypted: "true"
```
- We have to mention the storage class name in PersistentVolumeClaim definition file by using `storageClassName` attribute.
- If we are using the storage class, then we don't have to create the Persistent Volume manually. It will be created automatically by the storage class.
- Also there is one option available in Storage Class `volumeBindingMode` we can set it to `WaitForFirstConsumer` so that the PV will be created only when the PVC is created.

Date of Commit: 12/03/2024