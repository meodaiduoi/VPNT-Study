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
# Check po all
```
k get po -o wide sh
NAME                    READY   STATUS    RESTARTS   AGE   IP           NODE           NOMINATED NODE   READINESS GATES
blue-667bf6b9f9-dplnh   1/1     Running   0          63s   10.244.0.4   controlplane   <none>           <none>
blue-667bf6b9f9-rxr5b   1/1     Running   0          63s   10.244.1.2   node01         <none>           <none>
blue-667bf6b9f9-zwk45   1/1     Running   0          63s   10.244.1.3   node01         <none>           <none>
```