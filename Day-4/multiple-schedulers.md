## Multiple Schedulers

- Kubernetes ships with a default scheduler. If the default scheduler does not suit your needs you can implement your own scheduler. Moreover, you can even run multiple schedulers simultaneously alongside the default scheduler and instruct Kubernetes what scheduler to use for each of your pods.
- To run multiple schedulers, you need to pass the `--scheduler-name` flag to the kube-scheduler component. This flag specifies the name of the scheduler. You can run multiple kube-scheduler components with different names.
- We can create a configuration file to run multiple schedulers. A minimal configuration file looks as follows:
```yaml
apiVersion: kubescheduler.config.k8s.io/v1beta2
    kind: KubeSchedulerConfiguration
    profiles:
      - schedulerName: custom-scheduler
    leaderElection:
      leaderElect: false
```
- The above configuration file will run an instance of kube-scheduler with the name `my-scheduler`.
- **leaderElection:** If we are using mutiple copies of the same scheduler, we need to enable leader election to ensure that only one instance of the scheduler is active at a time. This is to prevent multiple schedulers from scheduling the same pod.
- To assign a pod to a specific scheduler, you need to add the `schedulerName` field to the pod definition file. The `schedulerName` field specifies the name of the scheduler that should be used to schedule the pod.
- The `schedulerName` field is added to the `spec` section of the pod definition file.
- Use the below syntax to add the `schedulerName` field to a pod definition file:

  ```yaml
  apiVersion: v1
  kind: Pod
  metadata:
    name: myapp-pod
  spec:
      containers:
      - name: myapp-container
          image: nginx
      schedulerName: custom-scheduler
```

- The above pod will be scheduled by the `custom-scheduler`.
- To get the list of all schedulers, use the below command:

```bash
kubectl get schedulers
```
- To get the details of a specific scheduler, use the below command:

```bash
kubectl describe scheduler custom-scheduler
```
- To delete a scheduler, use the below command:
    
```bash
kubectl delete scheduler custom-scheduler
```

Refer to the [official documentation](https://kubernetes.io/docs/tasks/extend-kubernetes/configure-multiple-schedulers/) for more information on multiple schedulers.

Date of Commit: 06/03/2024