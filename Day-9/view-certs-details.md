## View the details of the certificates

- If we set up the cluster manually in the Hard Way, We have to use `cat /etc/systemd/system/kube-apiserver.service` to view the details of the certificates of the `kube-apiserver`.
- For the remaining components also, The same path can be used to view the details of the certificates. Just replace the `kube-apiserver` with the component name.
- If we set up the cluster using `kubeadm`, We can use the `cat /etc/kubernetes/manifests/kube-apiserver.yaml` to view the details of the certificates of the `kube-apiserver`. Replace the `kube-apiserver` with the component name to view the details of the remaining components.
- **openssl x509 -in /etc/kubernetes/pki/certname.crt -text -noout** can be used to view the details of the certificates.

### Viewing Logs for troubleshooting TLS issues:

- We can use the `journalctl -u kube-apiserver` for Manual setup.
- For `kubeadm` setup, We can use the `kubectl logs kube-apiserver-master -n kube-system` to view the logs of the `kube-apiserver`.
- Replace the `kube-apiserver` with the component name to view the logs of the remaining components.
- We can also go one step down and use `docker logs container-id` to view the logs of the container.

Date of Commit: 11/03/2024