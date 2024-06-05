# Update replica config

``` sh
kubectl replace -f <existing-replica-rule.yaml>
# or update without needed to edit the exsting file
kubectl scale --replicas=6 -f <existing-replica-rule.yaml>
# even more you can change the "kind" of existing rule
kubectl scale --replica=6 replicaset <existing-replica-rule.yaml>
```
# Deleting replicaset
```
kubectl delete replicaset <replicaset_name>
```
