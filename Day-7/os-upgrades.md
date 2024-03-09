## Operating System Upgrades

- If we down any node for OS upgrades, The applications running on that node will be not available.
- So we need to plan the OS upgrades carefully.
- There are three commands to do in in safe way.
    - `kubectl drain <node-name>`: This command will evict all the pods from the node and mark it as unschedulable. The pods will be rescheduled to other nodes.
    - `kubectl uncordon <node-name>`: This command will mark the node as schedulable again.
    - `kubectl cordon <node-name>`: This command will mark the node as unschedulable.

Date of Commit: 09/03/2024