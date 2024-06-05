#Kubernetes 
# Ref:
[Replicaset-Recap](https://icenter.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/learn/lecture/14298658#overview)
# Replication controller:
``` YAML
# rc-def.yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: myapp-rc
  labels:
    app: myapp
    type: front-end
spec: # This is 'replica Pod section'
  template:
    metadata:
      name: myapp-pod
      label:
        app: myapp
        type: front-end
    spec:
      containers:
      - name: nginx-container
        image: nginx
  replicas: 3 # number of replicas
```

Running replica

``` sh
kubectl create -f rc-def.yaml 
```

get replication controller

``` sh
kubectl get replicationcontroller
```

# Replication set:
``` YAML
# replicaset-def.yaml
apiVersion: v1
kind: ReplicaSet
metadata:
  name: myapp-replicaset
  labels:
    app: myapp
    type: front-end
spec: # This is 'replica Pod section'
  template:
    metadata:
      name: myapp-pod
      label:
        app: myapp
        type: front-end
    spec:
      containers:
      - name: nginx-container
        image: nginx
  replicas: 3 # number of replicas
  selector: # 
    matchLabels:
      type: front-end
```

Running replica

``` sh
kubectl create -f replicaset-def.yaml
```

Get replicaset

``` sh
kubectl get replicaset 
```

For managing replica: [[Scaling & Managing replica]]
# Labels and Selector
