#Kubernetes 
# Ref:
[kubernetes kubectl run vs create and apply](https://stackoverflow.com/questions/48015637/kubernetes-kubectl-run-vs-create-and-apply)
## Applying Kubernetes Objects: Options and Benefits

**Applying Methods:**

- **Generators (Run, Expose):** Quick testing for container functionality.
- **Imperative (Create):** Direct object creation for specific needs.
- **Declarative (Apply):** Version-controlled application, ensuring data accuracy and rollbacks.

**Object Hierarchy and Flexibility:** These layers offer flexibility to manage containerized applications in Kubernetes.

- **Pods:** Group related containers for efficiency.
- **ReplicaSets:** Maintain desired pod replicas within the cluster.
- **Deployments:** Manage different pod versions and facilitate rollbacks.

**For example and command usage and common template refer to:** [[Create, Run and Apply]]

