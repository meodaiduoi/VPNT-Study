#Kubernetes 
## Ref
[What is the difference between a pod and a deployment?](https://stackoverflow.com/questions/41325087/what-is-the-difference-between-a-pod-and-a-deployment)
## Kubernetes has three **Object Types** you should know about:

- **Pods** - runs one or more closely related containers
- **Services** - sets up networking in a Kubernetes cluster
- **Deployment** - Maintains a set of identical pods, ensuring that they have the correct config and that the right number of them exist.

**Pods:**

- Runs a single set of containers
- Good for one-off dev purposes
- Rarely used directly in production

**Deployment:**

- Runs a set of identical pods
- Monitors the state of each pod, updating as necessary
- Good for dev
- Good for production