``` sh
# Create
kubectl create -f deployment
```

``` sh
kubectl get deploy
```

``` sh
# Update
kubectl apply -f <deployment-definition.yml>
kubectl set image deployment/myapp-deployment nginx=nginx:<version>
```

``` sh
# Status
kubectl rollout status <deployment/myapp-deployment>
kubectl rollout history <deployment/myapp-deployment>
```

``` sh
kubectl rollout undo <deployment/myapp-deployment>
```