## Authentication

- Authentication is the process of verifying the identity of the user.
- It includes authenticating admins accessing the cluster, developer testing the application, end-users accessing the application and other services or application accessing our cluster for some integration purpose.

### Authentication in Kubernetes

- Most of time we need to have authenticate with `kube-apiserver` to access the cluster.
- There is many ways to authenticate with kube-apiserver.
- The two most basic ways are:
    - Static Password File
    - Static Token file
- We need to have our users password or token along with username and user-id in a file.
- Then we have to pass the file to the kube-apiserver using the `--basic-auth-file` or `--token-auth-file` flags.
- For static password file, we can authenticate using the `curl -v -k https://master-node-ip:6443/api/v1/pods -u "user1:password123" ` command.
- For static token file, we can authenticate using the `https://master-node-ip:6443/api/v1/pods --header "Authorization: Bearer KpjCVbI7rCFAHYPkBzRb7gu1cUc4B" "Authorization

### Important Note

- This is not a recommended authentication mechanism
- Consider volume mount while providing the auth file in a kubeadm setup
- Setup Role Based Authorization for the new users

### Other notes about kubectl
- We can't create a user using the `kubectl` command.
- But we do have a concept called `ServiceAccount` which is used to authenticate the pods to the API server. We can create a `ServiceAccount` using the `kubectl` command.


Date of Commit: 10/04/2024