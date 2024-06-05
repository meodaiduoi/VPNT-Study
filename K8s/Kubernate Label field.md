#Kubernetes #label #selector
### Ref: 
[Label & Selector](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)
[Kubernates service](https://www.geeksforgeeks.org/kubernetes-service/)
# Label & Selector 

**Labels and Selectors** are the standard method to group things together in Kubernetes. We can filter the objects based on the criteria like class, kind, and functions.

- Labels are the properties attached to each item/object.
- Selector helps us to filter the items/objects which have labels attached to them.

Labels and Selectors are mentioned on the configuration file of the deployments and services. They are used to connect [kubernetes services](https://www.geeksforgeeks.org/kubernetes-service/) with a [kubernetes pod.](https://www.geeksforgeeks.org/kubernetes-pods/)
## Label rule and example template

Kubernetes labels are key-value pairs with rules:

- **Key:**
    - Two parts (optional prefix and name) separated by "/".
    - Name (required): 63 characters max, starts/ends with alphanumeric, uses .-_.
    - Prefix (optional): DNS subdomain format (max 253 characters).
    - Prefixes are required for automation adding labels (e.g., kube-scheduler).
    - Prefixes `kubernetes.io/` and `k8s.io/` are reserved for Kubernetes.
- **Value:**
    - 63 characters max (can be empty).
    - If not empty, starts/ends with alphanumeric, uses .-_.

## Template for Pods / Deployments:

``` yaml
# The deployment is given labels in the format below:
"metadata":   
{  
 "labels":   
 {  
   "key1" : "value1",  
   "key2" : "value2"  
 }  
}
```

``` yaml
# Example usage
apiVersion: v1
kind: Pod
metadata:
  name: label-demo
  labels: # Belong to metadata
    environment: production
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

Kubernetes labels let users organize objects with their own labels (tags), independent of system structure. This is flexible for complex deployments (multi-part, multi-version) and avoids rigid hierarchies imposed by the system.

## Service
The service identifies the pods and deployments using selectors in the format below:

``` yaml
"selector":  
 {  
    "key" : "value"  
 }
```

### Example
``` yaml 
apiVersion: v1
kind: Pod  
metadata:  
  name: tomcat  
  labels:  
    deployemnt: deployemnet-java # Add label to Pod
spec:  
  containers:  
  - name: tomcat  
    image: tomact:latest  
    ports:  
      - containerPort: 8080  
        name: http-deplyment-port  
  
--- 
# Serivce
apiVersion: v1  
kind: Service  
metadata:  
  name:tomcat-service  
spec:  
  selector:  
    deployemnt: deployemnet-java  # Select label deployemnt: deployemnet-java 
  ports:  
  - name: name-of-service-port  
    protocol: TCP  
    port: 80  
    targetPort:http-deplyment-port
```

For example, we can see that instead of using the ****“targetPortnumber”**** you can use the name of the container as mentioned below. The target port is the port number that the service or pod is forwarding requests to.

![[Pasted image 20240605171202.png]]

**Service without selector:**
# Common labels:

- `"release" : "stable"`, `"release" : "canary"`
- `"environment" : "dev"`, `"environment" : "qa"`, `"environment" : "production"`
- `"tier" : "frontend"`, `"tier" : "backend"`, `"tier" : "cache"`
- `"partition" : "customerA"`, `"partition" : "customerB"`
- `"track" : "daily"`, `"track" : "weekly"`

These are examples of [commonly used labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/common-labels/); you are free to develop your own conventions. Keep in mind that label Key must be unique for a given object.

