## Editing Pod

We **CANNOT** edit specifications of an existing POD other than the below.

- spec.containers[*].image
- spec.initContainers[*].image
- spec.activeDeadlineSeconds
- spec.tolerations

Date of Commit: 06/03/2024