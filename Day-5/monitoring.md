## Monitoring in K8S

Normally there is no bulit-in monitoring in K8S. But there are many Open Source tools that can be used to monitor K8S. Some of them are:
- Metrics Server
- Prometheus
- Grafana
- Kibana
- ElasticSearch
- Datadog

### Heapster vs Metrics Server

Heapster was the original tool for monitoring K8S. It was deprecated in 2018 and replaced by Metrics Server. Metrics Server is a scalable, efficient source of container resource metrics for K8S built-in autoscaling pipelines.

### Metrics Server

- We can use Metrics Server to monitor the resource usage of the pods and nodes in the K8S cluster.
- It collects the CPU and memory usage of the pods and nodes in the K8S cluster.

#### Installing Metrics Server

- To enable Metrics Server in minikube, we can use the following command:
  ```bash
  minikube addons enable metrics-server
  ```

- To install Metrics Server in a K8S cluster, we can use the following command:
```bash
git clone https://github.com/kubernetes-incubator/metrics-server.git
kubectl apply -f metrics-server/deploy/1.8+/
```
#### Metrics Visualization

- To visualize the metrics on node, we can use the following command:
```bash
kubectl top node
```

- To visualize the metrics on pod, we can use the following command:
```bash
kubectl top pod
```

Date of Commit: 07/03/2024