## Imperative vs Declarative Commands

### Imperative Commands

- Imperative commands are those commands which tell the computer how to do something.

### Declarative Commands

- Declarative commands are those commands which tell the computer what to do.

### Imperative vs Declarative Commands Example

- **Imperative Commands**: `kubectl run mypod --image=nginx` is an imperative command which tells the computer to run a pod with the name `mypod` and the image `nginx`.

- **Declarative Commands**: `kubectl apply -f pod-definition-file.yaml` is a declarative command which tells the computer to create a pod with the definition file `pod-definition-file.yaml`.

- **Use Cases**: 

    - **Imperative Commands**: Imperative commands are useful when you want to do something quickly. For example, if you want to run a pod quickly, you can use imperative commands.

    - **Declarative Commands**: Declarative commands are useful when you want to do something in a controlled way. For example, if you want to create a pod with a specific configuration, you can use declarative commands.


### Imperative Commands Examples

- **Create Pod**: `kubectl run mypod --image=nginx`
- **Create Service**: `kubectl expose pod mypod --port=80 --type=NodePort`
- **Create Deployment**: `kubectl create deployment myapp-deployment --image=nginx`
- **Scale Deployment**: `kubectl scale deployment myapp-deployment --replicas=3`
- **Update Deployment**: `kubectl set image deployment/myapp-deployment myapp-container=nginx:1.9.1`
- **Delete Resources**: `kubectl delete pod mypod`
- **Create resource**: `kubectl create -f pod-definition-file.yaml`
- **Replace resource**: `kubectl replace -f pod-definition-file.yaml`
- **Delete resource**: `kubectl delete -f pod-definition-file.yaml`


### Declarative Commands Examples

- **Create Pod**: `kubectl apply -f pod-definition-file.yaml`
- **Create Service**: `kubectl apply -f service-definition-file.yaml`
- **Create Deployment**: `kubectl apply -f deployment-definition-file.yaml`
- **Scale Deployment**: `kubectl apply -f deployment-definition-file.yaml`          
- **Update Deployment**: `kubectl apply -f deployment-definition-file.yaml`

Commit Date: 03/03/2024