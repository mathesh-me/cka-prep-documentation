## containerd

- During K8S first days, Docker was the only container runtime available.
- So, All the other container runtimes were also wanted to be supported by K8S.
- So K8S community came up with a standard called CRI (Container Runtime Interface).
- CRI is a standard that allows K8S to support multiple container runtimes.
- And also all the container runtimes that want to be supported by K8S should implement the CRI standard and Open Container Initiative (OCI) runtime standards.
- But Docker was not adhered to OCI standards. So, K8S community provided temporary support for Docker using a tool called `dockershim`.

### containerd history

- Initally containerd was a part of Docker providing support for the Docker runtime runc.
- But later it was moved out of Docker and became a separate project.
- It was donated to CNCF (Cloud Native Computing Foundation) in 2017. 


### Containerd

- Containerd is an industry-standard core container runtime.

### Three different commands used in K8S for CRI compliant runtimes
- **ctr**: It is a client for containerd comes up with containerd installation, Used for debugging. It is not used for container management.
- **nerdctl**: It is developed by containerd used for development. It works just like Docker we can create and manage containers and images.
- **crictl**: It is developed by K8S community to interact with CRI compliant runtimes. It is used for debugging purposes.

Commit Date: 02/03/2024