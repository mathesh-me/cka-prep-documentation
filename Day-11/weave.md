## WeaveWorks

### WeaveWorks Working:

- Weave deploys a agent in every node of the cluster.
- Then the agnets will communicate with each other to form a share information about pods, nodes and other objects.
- And also weave will deploy a network interface in each node like bridge network interface.
- From that weave network interface, all the pods can communicate with each other.
- If pod in Node A wants to send data to pod in Node B, The pod will send data and agent in Node A will encapsulate the data and send it to the agent in Node B. Then the agent in Node B will decapsulate the data and send it to the pod in Node B.

### Installing WeaveWorks:

- We can install weave by running the following command:
```bash
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
```
- It will deploy weave network as a daemonset in all the nodes. Pods will be deployed in kube-system namespace.
- We can also view the logs of pods by using their appropriate names.

Date of Commit: 13/03/2024