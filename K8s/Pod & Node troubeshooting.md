#Kubernetes #Docker 

Ref: 

# Troubleshooting with kubectl

In Module [2](https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/), you used the kubectl command-line interface. You'll continue to use it in Module 3 to get information about deployed applications and their environments. The most common operations can be done with the following kubectl subcommands:

- **`kubectl get`** - list resources
- **`kubectl describe`** - show detailed information about a resource
- **`kubectl logs`** - print the logs from a container in a pod
- **`kubectl exec`** - execute a command on a container in a pod

## explain & api-resource

For checking correct namespace

``` sh
kubectl api-resource | grep <namespcae>
# ex:
kubectl api-resource | grep replicaset
```

Explain the correct version
``` sh
kubectl explain <resource>
# ex
kubectl explain replicaset
```