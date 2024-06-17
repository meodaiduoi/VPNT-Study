#Kubernetes #Devop 
## Example Template
```Yaml
apiVersion: apps/v1  
kind: DaemonSet # DaemonSet kind
metadata:  
  name: fluentd  
  namespace: kube-system  
  labels:  
    k8s-app: fluentd  
spec:  
  selector:  
    matchLabels:  
      name: fluentd  
  template:  
    metadata:  
      labels:  
        name: fluentd  
    spec:  
      containers:  
      - name: fluentd  
        image: fluentd:latest
```

## Create daemon set using --dry-run
Same as creating deployment file but we have to remove some part out of yaml file

``` sh
create deployment <name> --image=<image_name> -n <namespace> --dry-run=client -o yaml > <filename>.
```

Remove `replicas` and `strategy` attribute and change `kind:Deployment` to `kind:DaemonSet` to make it into DaemonSet file

```yaml
apiVersion: apps/v1
#kind: Deployment
kind: DaemonSet
metadata:
  creationTimestamp: null
  labels:
    app: test
  name: test
  namespace: test
spec:
#  replicas: 1 // Remove replicas attrib
  selector:
    matchLabels:
      app: test
#  strategy: {} // Remove strategy attrib
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: test
    spec:
      containers:
      - image: nginx
        name: nginx
        resources: {}
status: {}
```

Statis Pods vs DaemonSets

| Static Pods                                    | DaemonSets                                        |
| ---------------------------------------------- | ------------------------------------------------- |
| Create buy the Kubelet                         | Created by Kube-API server (DaemonSet Controller) |
| Deploy Control Plane Components as Static Pods | Deploy monitoring Agents, Logging Agents ib bides |
| Ignored by the kube-scheduler                  | Ignored by the kube-scheduler                     |
