## How K8S implements DNS

- By deafult whenver we deploy a pod K8S automatically update the /etc/resolv.conf file with the DNS server IP address.
- The DNS server IP address will be the IP address of the kube-dns service.
- The kube-dns service will be running in the kube-system namespace.
- The cluster-dns will be running as a pod in the kube-dns service. It will ahve a execuatble for ./Coredns.
- We can find CoreDNS configuration file in /etc/coredns/Corefile.
- We can also find the CoreDNS configuration file in the configmap of the kube-dns service.
```conf
.:53 {
errors
health
kubernetes cluster.local in-addr.arpa ip6.arpa {
pods insecure
upstream
fallthrough in-addr.arpa ip6.arpa
}
prometheus :9153
proxy . /etc/resolv.conf ## If the DNS name is not found in the cluster, then it will look into the /etc/resolv.conf file.
cache 30
reload
}
```
- We can find the Cluster DNS Ip and domain name in the `/var/lib/kubelet/config.yaml file`.
- `search default.svc.cluster.local svc.cluster.local cluster.local` is added as search by default in the `/etc/resolv.conf` fileo f pods when created by K8S.

Date of Commit: 13/03/2024