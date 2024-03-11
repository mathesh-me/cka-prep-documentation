## Configure TLS certificates for Kubernetes Cluster

### Commands to Generate Certificates:

There are various methods for generating certificates.
- openssl
- cfssl
- easyrsa

Here, we are using the `openssl` command to generate the certificates.

#### Step 1: Generate Certificate Key:
```bash
$ openssl genrsa -out ca.key 2048
```
#### Step 2: Generate Certificate Signing Request:
```bash
$ openssl req -new -key ca.key -subj "/CN=kube-ca" -out ca.csr
```
#### Step 3: Sign the Certificate:
```bash
$ openssl x509 -req -in ca.csr -signkey ca.key -out ca.crt
```

- The above commands will generate the `ca.key` and `ca.crt` files.
- Now we generated the CA certificates for the Kubernetes cluster.
- We can use these certificates to sign the other certificates.

### Generate Certificates for Other Kubernetes Servers and Clients:

#### Step 1: Generate Certificate Key:
```bash
$ openssl genrsa -out server.key 2048
```

#### Step 2: Generate Certificate Signing Request:
```bash
$ openssl req -new -key server.key -subj "/CN=kube-apiserver" -out server.csr
```

#### Step 3: Sign the Certificate:
```bash
$ openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -out server.crt
```

- The above commands will generate the `server.key` and `server.crt` files.
- We signed the server certificate with the CA certificate.
- This same steps can be followed to generate the other and client certificates.

### Making the normal user as the cluster-admin:

- We are generating the Certificates for the user. But How Kubernetes will recognize the user as the cluster-admin?
- We can make the user by adding the user to the `system:masters` group.
- The `system:masters` group is the cluster-admin group in the Kubernetes cluster.
- We just have to add /OU=system:masters when we ar generating the certificate signing request. Like this:
```bash
$ openssl req -new -key admin.key -subj "/CN=admin/O=system:masters" -out admin.csr
```

### Naming Conventions for Certificates:

- The naming conventions for the certificates are important.
- The certificates should be named with the following format:
    - `kube-apiserver`, `system:kube-controller-manager`, `system:kube-scheduler`, `system:nodename for kubelet client access`, `nodename for  server access`, `kube-proxy`, `admin`, `etcd-server`.
- But for kube-api-server, There are many names like `kube-apiserver`, `kubernetes`, `kubernetes.default`, `kubernetes.default.svc`, `kubernetes.default.svc.cluster.local`.
- So when we are make a csr for the kube-apiserver, we have to add all the names in the subject alternative names.
- Best practice is to add all the alternative names in a separate file and then use that file in the csr command.
- Example:
```bash
$ openssl req -new -key kube-apiserver.key -subj "/CN=kube-apiserver" -config kube-apiserver.cnf -out kube-apiserver.csr
```
- We have to add the alternative names in the `kube-apiserver.cnf` file.

### Mention the Certificate Paths in the Configuration Files:

- After generating the certificates, we have to mention the certificate paths in the configuration files.
- Depends upon our cluster setup, we have to mention the certificate paths in the following files:
    - `/etc/kubernetes/manifests/kube-apiserver.yaml`
    - `/etc/kubernetes/manifests/kube-controller-manager.yaml`
    - `/etc/kubernetes/manifests/kube-scheduler.yaml`
    - `/etc/kubernetes/kubelet.conf`
    - `/etc/kubernetes/kube-proxy.conf`
    - `/etc/kubernetes/admin.conf`
    - `/etc/etcd/etcd.conf`

- We have to mention the certificate paths in the `--tls-cert-file` and `--tls-private-key-file` flags.
- We also have to mention the CA certificate path in the `--client-ca-file` flag.


Date of Commit: 11/03/2024