#Kubernetes 

``` yaml
apiVersion: v1
kind: Pod / Deployment / Service
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end
spec:
  containers: # List / Arr
  - name: nginx-container # 1st item in list
    image: nginx
  - name: busybox # 2nd item in list
    image: busybox
```

For [[Kind Pods, Services, Deployment]] (kind) we recommended to use "Deployment" for most of the case

Labels are intended to be used to specify identifying attributes of objects that are meaningful and relevant to users, but do not directly imply semantics to the core system, `label` notation can be found:  [[Kubernate Label field]]

[[Replication YAML structure]]
Sample `hellokube.yaml` can be found here:

There are 3 kinds of `kind` that can be found here: [[Kind Pods, Services, Deployment]]