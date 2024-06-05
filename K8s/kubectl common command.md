#Kubernetes #kubectl

# Common Usage

**get pod**

``` sh
kubectl get po -A
# or
kubectl get pods -A
```

**Use this deployment file for Hello World application.**

```
kubectl create -f helloworld.yaml
```
****Expose the deployment as Node port to view in browser.**

```
kubectl expose deployment helloworld --type=NodePort
```

**Open your deployment in a browser!!**

```
minikube service helloworld
```

**Describe pods**

```
kubectl describe po
kubectl describe pods
```

**Edit a pods**
Update the pod-definition file and use `kubectl apply` command or use `kubectl edit pod redis` command.

**Run a pod**

``` bash
kubectl create -f <file.yaml>
kubectl run <pod name> --image <image>
ex: kubectl run nginx-test --image nginx
```
# Generate a dry-run template file

``` sh
kubectl run <pod name> --image=<image name> --dry-run=<client/server> -o yaml > filename.yaml

// ex: kubectl run redis --image=redis --dry-run=client -i yaml > redis.yaml
```
run dry-run output
``` sh
kubectl create -f redis
```

For more example visit:
[[Generating template using --dry-run]]
# Troubleshooting your cluster
[[Pod & Node troubeshooting]]