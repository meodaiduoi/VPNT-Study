#Kubernetes #namespace 

# **Example Commands:**

**Creating a Namespace:**

```
kubectl create namespace dev
```

**Applying Resource Quotas:**

```
kubectl apply -f quota.yaml -n dev
```

**Defining RBAC Policies:**

```
kubectl apply -f rbac.yaml -n dev
```

**Adding Labels and Annotations:**

```
kubectl annotate namespace dev description="Development Namespace"
```

**Listing and Managing Namespaces:**

``` sh
kubectl get namespaces <name of namespace (opt)>

kubectl describe namespace <name of namespace (opt)>
```
