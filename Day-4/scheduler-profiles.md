## Scheduler Profiles

- A scheduling Profile allows you to configure the different stages of scheduling in the kube-scheduler. Each stage is exposed in an extension point. Plugins provide scheduling behaviors by implementing one or more of these extension points.
- You can configure a single instance of kube-scheduler to run multiple profiles.

### Scheduler Workflow

- It includes the following stages:
  - **Prioritization:** The prioritization stage is responsible for ranking the remaining nodes based on the priority function.
  - **Filtering:** The filtering stage is responsible for removing nodes that are not suitable for the pod.
  - **Scoring:** The scoring stage is responsible for scoring the remaining nodes based on the scoring function.
  - **Binding:** The binding stage is responsible for selecting the best node and binding the pod to it.

- Normally each stage uses some plugins to perform the required operations. You can disable specific default plugins or enable your own.
- Plugins will be plugged into extension points in the kube-scheduler workflows.
- There are many extension points attached to scheduler workflow stages.
- For each extension point, you could disable specific default plugins or enable your own. For example:
```yaml
apiVersion: kubescheduler.config.k8s.io/v1
kind: KubeSchedulerConfiguration
profiles:
    -- schedulerName: my-scheduler
    plugins:
      score:
        disabled:
        - name: PodTopologySpread
        enabled:
        - name: MyCustomPluginA
          weight: 2
        - name: MyCustomPluginB
          weight: 1
```

- You can use * as name in the disabled array to disable all default plugins for that extension point. This can also be used to rearrange plugins order, if desired.

### Multiple Profiles

- Normally we use single file for ksingle ube-scheduler configuration. But we can use multiple profiles in a single file.
- A minimal configuration looks as follows:
```yaml
apiVersion: kubescheduler.config.k8s.io/v1
kind: KubeSchedulerConfiguration
profiles:
  - schedulerName: my-scheduler
    plugins:
      score:
        disabled:
        - name: PodTopologySpread
        enabled:
        - name: MyCustomPluginA
          weight: 2
        - name: MyCustomPluginB
          weight: 1
  - schedulerName: my-scheduler2
    plugins:
      score:
        disabled:
        - name: PodTopologySpread
        enabled:
        - name: MyCustomPluginA
          weight: 2
        - name: MyCustomPluginB
          weight: 1
```

- The above configuration file will run two instances of kube-scheduler with the names `my-scheduler` and `my-scheduler2`.
- To assign a pod to a specific scheduler, you need to add the `schedulerName` field to the pod definition file. The `schedulerName` field specifies the name of the scheduler that should be used to schedule the pod.

Refer to the [official documentation](https://kubernetes.io/docs/tasks/extend-kubernetes/configure-multiple-schedulers/) for more information on multiple schedulers.

Date of Commit: 06/03/2024