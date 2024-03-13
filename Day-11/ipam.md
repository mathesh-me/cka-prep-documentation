## IP Address Management (IPAM)

- The important responsibility of CNI plugins is it must manange IP allocation on pods.
- When creating a plugin we can create a separate file for storing IP address and mention the file path in the plugin script file. In that way we have to create a IP address file on each node and we have to manage the IP address file on each node. It is not a easy thing.
- So what plugin providers do is, they have some plugins to manage the IP address. One is `host-local` and another one is `dhcp`.
- `host-local` plugin will manage the IP address by itself. It will allocate the IP address from the range of IP address that we have mentioned in the configuration file.
- `dhcp` plugin will allocate the IP address from the DHCP server. It will communicate with the DHCP server and allocate the IP address to the pods.
- Example using Host-Local plugin:
  - We can use the following configuration file to use the host-local plugin:
```json
{
"cniVersion": "0.2.0",
"name": "mynet",
"type": “net-script",
"bridge": "cni0",
"isGateway": true,
"ipMasq": true,
"ipam": {
"type": "host-local",
"subnet": "10.244.0.0/16",
"routes": [
{ "dst": "0.0.0.0/0" }
]
}
}
```

Date of Commit: 13/03/2024