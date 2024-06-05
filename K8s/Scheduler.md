## Ref:
[Assigning Pods to Nodes](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/)
## Assign nodeName manually[*](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#nodename)
(not recommended)

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx
  nodeName: kube-01 # Assign node manually
```

#### Warning:

`nodeName` is intended for use by custom schedulers or advanced use cases where you need to bypass any configured schedulers. Bypassing the schedulers might lead to failed Pods if the assigned Nodes get oversubscribed. You can use [node affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#node-affinity) or the [`nodeSelector` field](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#nodeselector) to assign a Pod to a specific Node without bypassing the schedulers.


## NodeSelector[*](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#nodeselector)
