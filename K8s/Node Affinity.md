Type of node affinity

**Example templates**

``` yaml
affinity:  
  nodeAffinity:  
    requiredDuringSchedulingRequiredDuringExecution:  
      nodeSelectorTerms:  
      - matchExpressions:  
        - key: <label-key>  
          operator: In  
          values:  
          - <label-value>
```

**Example config yaml**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  affinity: # Affinity
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution: # Affinity rule
        nodeSelectorTerms:
        - matchExpressions:
          - key: disktype
            operator: In
            values:
            - ssd            
  containers:
  - name: nginx
    image: nginx
    imagePullPolicy: IfNotPresent
```
## RequiredDuringSchedulingRequiredDuringExecution
**Hard rule**
The pod must be scheduled on a node that complies with the node affinity criteria  If no nodes in the cluster satisfy the rule, then the pod will remain unscheduled. If the node labels are changed in the future the pod will be evicted.

```yaml
affinity:  
  nodeAffinity:  
    requiredDuringSchedulingRequiredDuringExecution:  
      nodeSelectorTerms:  
      - matchExpressions:  
        - key: <label-key>  
          operator: In  
          values:  
          - <label-value>
```

In this case, the label key-value pair specified in the “nodeSelectorTerms” prevents the pod from being scheduled on nodes that do not have it.

(Only be scheduled on nodeSelector match and will be evicted on rule change)
## RequiredDuringSchedulingIgnoredDuringExecution

**Hard rule**
The pod will be scheduled only if the pod labels are matched with the node labels. If the node labels are changed in the future the pod will not be evicted.
```yaml
affinity:  
        nodeAffinity:  
         requiredDuringSchedulingIgnoredDuringExecution:  
           nodeSelectorTerms:  
           - matchExpressions:  
             - key: <label-key>  
               operator: In  
               values:  
               - <label-value>
```

(Only be scheduled on nodeSelector match but will not be shutdown on rule change)
## PreferredDuringSchedulingIgnoredDuringExecution

**Soft rule:**
This specifies the primary way for scheduling a node for a pod in accordance with the node affinity rule. The pod will still be scheduled on a node that does not match with the rule if none of the cluster’s nodes do.
```yaml
affinity:  
  nodeAffinity:  
    preferredDuringSchedulingIgnoredDuringExecution:  
    - weight: 100  
      preference:  
        matchExpressions:  
        - key: <label-key>  
          operator: In  
          values:  
          - <label-value>
```

In this case, the pod will be scheduled on a node that has the label key-value pair specified in the “match expressions” section. **If nodes do not meet this requirement, the pod will still be scheduled on a different node.**

(Any node with best nodeSelector match)