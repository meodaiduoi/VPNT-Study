# Service structure

``` Yaml
apiVersion: v1  
kind: Service  
metadata:  
  name: my-service  
spec:  
  selector:  
    app: nginx  
  type: LoadBalancer  
  ports:  
    - protocol: TCP  
      port: 8080  
      targetPort: 80
```
## Services Without Selectors

This type of service will be exposed to all the pods in the kubernetes cluster. If the service is having selectors then that service will be exposed to only certain pods in the kubernetes cluster. We can use this special case of pods for different situations as the following:

### Example

``` yaml
apiVersion: v1  
kind: Service  
metadata:  
  name: tomcat-service  
spec:  
  ports:  
    - protocol: TCP  
      port: 80  
      targetPort: 8080
```

You can map the service to the required object by using the network address and port with the help of the Endpoint slice object manually.