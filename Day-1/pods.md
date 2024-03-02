## Pods

- Pods are the smallest deployable units in Kubernetes. A Pod is a group of one or more containers, with shared storage/network resources, and a specification for how to run the containers.

### Pods important points

- Let's I deployed my application in a pod with single container. So what if my users increases and I need to scale my application. I can't scale my application by increasing the number of containers in a pod. So, I need to create another pod with the same application and then I can scale my application. So, Pods are the smallest deployable units in K8S.
- This doesn't mean that we can't have multiple containers in a pod. We can have multiple containers in a pod. The idea is that we shouldn't have use multiple containers in a pod for scaling Purpose. We should use multiple containers in a pod for the purpose of sharing resources Eg: Sidecar pattern.
- In simple words, We can launch different containers in a Pod. But not the same container for scaling purposes. We should create another pod for scaling purposes.

### Creating a Pod

- By using Command Line
```
kubectl run mypod --image=nginx
```
- By using YAML file
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
    containers:
    - name: mycontainer
        image: nginx
```
After creating a definition file, we can create a pod by using the following command
```
kubectl create -f pod-definition.yaml
```

Commit Date: 02/03/2024