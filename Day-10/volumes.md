## Volumes in K8S

- Volumes are the way to persist the data in the containers.

### Use case Pod with Volumes

- Let's say we have a Pod, We have some data inside the pod. If the pod is deleted, then the data inside the pod will also be deleted.
- We can use the volumes to persist the data inside the pod.
- We can mounth the path inside pod to the node's file system by using `hostpath`. So that the data inside the pod will be persisted even if the pod is deleted.
- We can also mount the path of pod to inside the container. So that the data inside the container will be persisted even if the container is deleted.
- **hostpath** is best in single node cluster. In multi node cluster, We have to use any other like **aws ebs**, **azure disk**, **gce persistent disk** or any other CSI supported storage.

Date of Commit: 12/03/2024