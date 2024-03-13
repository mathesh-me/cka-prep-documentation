## DNS

### Need for DNS

- Let's say we have to ping a server in our private network. We can ping it using `ping ip_addr_of_server`.
- But If We need to ping other servers in our network. Remembering the IP address of all the servers is not possible.
- So we can update the `/etc/hosts` file with the IP address and hostname of the servers. THis is called as Name Resolution.
- Example:
```bash
192.168.0.2 db_service
```
- But what if the servers in our Private network increases. Then we have to update the `/etc/hosts` file in all the servers.
- Doing this things is not possible in the large scale environment.
- So we can use a common DNS server to resolve the names to IP addresses.
- Then we can update the DNS server with the IP address and hostname of the servers. So we just need to update the DNS server with the IP address and hostname of the servers. Then all the servers in the network can resolve the names to IP addresses.
- Then we have to update the `/etc/resolv.conf` file with the DNS server IP address.
```bash
nameserver 192.168.0.10
```
- We can also add our ip address for hosts in `/etc/hosts` also for some testing servers that need not to be updated in DNS server.
- If the same host name is present in `/etc/hosts` and DNS server, then the `/etc/hosts` file will be given priority.
- We can check the priority of the name resolution in the `/etc/nsswitch.conf` file.
- For Domain names like google.com, we have to use the public DNS servers like 8.8.8.8

### Domain Names

- Format: `www.google.com`
- . is the root domain.
- com is the top level domain.
- google is the second level domain.
- www is the third level domain.

### Uisng `search` in `/etc/resolv.conf`:

- We can use the `search` option in the `/etc/resolv.conf` file to resolve the names to IP addresses.
- Example:
```bash
search example.com
```
- Then if we ping the server `db_service`, then the system will resolve the name to `db_service.example.com`

### DNS Record Types:

- A Record: It is used to map the hostname to the IP address.
- CNAME Record: It is used to map the hostname to another hostname.
- AAAA Record: It is used to map the hostname to the IPv6 address.

### nslookup

- We can use the `nslookup` command to resolve the names to IP addresses.
- Example:
```bash
nslookup db_service
```

### dig

- We can also use `dig` command to resolve the names to IP addresses.
- Example:
```bash
dig db_service
```

Date of Commit: 12/03/2024