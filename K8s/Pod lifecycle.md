[Pod life cyle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/)

# Pod status
``` sh
$ kubectl get pods # in the default namespace                                    
NAME                                READY   STATUS    RESTARTS      AGE
helloworld-76685c9c8b-p92fs         1/1     Running   1 (19h ago)   20h
nginx-deployment-77d8468669-77q7z   1/1     Running   1 (19h ago)   19h
nginx-deployment-77d8468669-dtx9n   1/1     Running   1 (19h ago)   19h
```

**Field notation**
`READY`: Total containers in POD/ Running containers in POD
`AGE`: how long your **pod** has been created and it's running.