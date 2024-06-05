#Kubernetes #namespace
# Ref:
[Namespace](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)
## Kubernetes Namespaces: Benefits and Best Practices

Namespaces provide isolation, resource control, and access management for workloads within a Kubernetes cluster. They act like virtual clusters for:

- **Isolated Teams & Workloads:** Teams have dedicated spaces for deployments and resource management.
- **Resource Governance:** Resource quotas limit resource consumption per namespace.
- **Fine-Grained Access Control:** RBAC policies grant access based on roles and responsibilities.
- **Scoped Objects:** Namespaces ensure unique identification of resources (pods, services, etc.)
- **Environment Segregation:** Separate environments (dev, staging, prod) within a single cluster.

**Best Practices:**

- **Clear Naming:** Use prefixes (dev-, stage-, prod-) for easy identification.
- **Resource Management:** Set quotas to prevent contention and ensure fair usage.
- **RBAC Policies:** Define and update access controls for security and compliance.
- **Labeling & Annotations:** Add metadata for programmatic management.
- **Scoping Efficiency:** Group related resources within a namespace for simpler management.

**Use Cases:**

- **Multi-Tenancy:** Isolated environments with access control for different teams or tenants.
- **Environment Segregation:** Separate dev, staging, and production environments in one cluster.
- **Microservice Partitioning:** Organize microservices by function or ownership for better management.
- **Rollback & Canary Deployments:** Isolate application versions for easier rollbacks.
## Initial namespaces[*](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/#initial-namespaces)

Kubernetes comes with four default namespaces:
- `default`: For quick use without creating a namespace.
- `kube-node-lease`: Stores node heartbeat information.
- `kube-public`: Readable by all clients, for shared cluster resources (convention, not enforced).
- `kube-system`: Holds objects created by Kubernetes itself.

### Viewing namespaces[*](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/#viewing-namespaces)

You can list the current namespaces in a cluster using:

```shell
kubectl get namespace
```

```
NAME              STATUS   AGE
default           Active   1d
kube-node-lease   Active   1d
kube-public       Active   1d
kube-system       Active   1d
```

### Checking objects are in namespace or not[*](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/#not-all-objects-are-in-a-namespace)

To see which Kubernetes resources are and aren't in a namespace:

```shell
# In a namespace
kubectl api-resources --namespaced=true

# Not in a namespace
kubectl api-resources --namespaced=false
```

**For namespace usage:** [[Namespace usage and examples]]
