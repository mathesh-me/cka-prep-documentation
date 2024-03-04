## Service in Kubernetes

In Kubernetes, a **Service** is a method for exposing a network application that is running as one or more Pods in your cluster.

### Important notes about Service

- If we create a Service it **automatically Spans across all the nodes** in the cluste which means that the Service is available on the entire cluster.

### Why do we need Service?

- Service Provide as a way to expose our application within cluster or outside the cluster.
- Pods in Kubernetes are mortal. They are created and destroyed dynamically. When a Pod dies, it is replaced by a new one. This means that the IP address of a Pod is not permanent. If you want to access a Pod, you need a way to discover it.
- Service provide a way to discover and access Pods. They provide a stable endpoint for accessing a set of Pods.
- Service also provide load balancing. If you have multiple Pods running the same application, a Service can distribute the traffic to all of them.

### Types of Service

- **ClusterIP**: Exposes the Service on a cluster-internal IP. Service only reachable from within the cluster.

- **NodePort**: Exposes the Service on each Node’s IP at a static port (the NodePort). A ClusterIP Service, to which the NodePort Service routes, is automatically created.

- **LoadBalancer**: Exposes the Service externally using a cloud provider’s load balancer. NodePort and ClusterIP Services, to which the external load balancer routes, are automatically created.

#### ClusterIP

- This is useful when you want to expose a Service to other apps running in the same cluster.
- For example, if you have a set of backend Pods that provide functionality to frontend Pods, you can create a Service of type ClusterIP to expose the backend Pods to the frontend Pods.
- The Service is only accessible from within the cluster.

- **definiton file**:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:

    selector:
        app: myapp
    
    ports:
        - protocol: TCP
        port: 80
        targetPort: 9376
```

- **Commands to Create service using the above file**:
    
    ```bash
    kubectl create -f service-definition-file.yaml
    kubectl get services
    ```

- **Imperative Command to Create Service**:

    ```bash
    kubectl expose pod mypod --port=80 --name myapp-service --type=ClusterIP
    ```

#### NodePort

- NodePort is the second most commonly used ServiceType. It exposes the Service on each Node’s IP at a static port (the NodePort). A ClusterIP Service, to which the NodePort Service routes, is automatically created.
- This means that the Service can be accessed from outside the cluster using `<NodeIP>:<NodePort>`.
- This is useful when you want to expose a Service to the outside world or when you want to access a Service from outside the cluster.
- For example, if you have a set of frontend Pods that provide a web application, you can create a Service of type NodePort to expose the frontend Pods to the outside world.
- The Service is accessible from outside the cluster.

- **definiton file**:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
    type: NodePort

    selector:
        app: myapp
    
    ports:
        - protocol: TCP
        port: 80
        targetPort: 9376
        nodePort: 30008
```

**Commands to Create service using the above file**:
    
```bash
kubectl create -f service-definition-file.yaml
kubectl get services
```

**Imperative Command to Create Service**:

```bash
kubectl expose pod mypod --port=80 --name myapp-service --type=NodePort
```

#### LoadBalancer

- LoadBalancer is the third most commonly used ServiceType. It exposes the Service externally using a cloud provider’s load balancer. NodePort and ClusterIP Services, to which the external load balancer routes, are automatically created.
- This means that the Service can be accessed from outside the cluster using the load balancer’s IP address.
- This is useful when you want to expose a Service to the outside world and you want to use a load balancer to distribute the traffic to the Service.
- For example, if you have a set of frontend Pods that provide a web application, you can create a Service of type LoadBalancer to expose the frontend Pods to the outside world and use a load balancer to distribute the traffic to the frontend Pods.
- The Service is accessible from outside the cluster.

- **definiton file**:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
    type: LoadBalancer

    selector:
        app: myapp
    
    ports:
        - protocol: TCP
        port: 80
        targetPort: 9376
```

**Commands to Create service using the above file**:
    
```bash
kubectl create -f service-definition-file.yaml
kubectl get services
```

**Imperative Command to Create Service**:

```bash
kubectl expose pod mypod --port=80 --name myapp-service --type=LoadBalancer
```
Commit Date: 03/03/2024