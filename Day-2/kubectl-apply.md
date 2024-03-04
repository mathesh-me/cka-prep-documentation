## kubectl apply working

- `kubectl apply` command is used to create and update resources in a Kubernetes cluster.

### Working Mechanism

- When you run `kubectl apply -f file.yaml`, it will create the resources defined in the file if they don't exist.
- If the resources already exist, it will update them to match the configuration in the file.
- It will check three things to do the working
    - Local definition file
    - Live configuration file in the cluster
    - Last applied configuration file in the cluster

Commit Date: 03/03/2024