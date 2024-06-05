Reference:
[Minikube](https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fdebian+package)
[Running helloworld kube](https://amdocs-1.gitbook.io/kubernetes-handbook/installation-and-running-mac-os/running-hello-world-application)

# Setup
for debian / ubuntu x86-64
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```

Open **Terminal** to start **Minikube**.

``` sh
inikube start
```

Check status of 'minikube'

``` sh
kubectl get all
```

## Manage your cluster

Pause Kubernetes without impacting deployed applications:

```shell
minikube pause
```

Unpause a paused instance:

```shell
minikube unpause
```

Halt the cluster:

```shell
minikube stop
```

Change the default memory limit (requires a restart):

```shell
minikube config set memory 9001
```

Browse the catalog of easily installed Kubernetes services:

```shell
minikube addons list
```

Create a second cluster running an older Kubernetes release:

```shell
minikube start -p aged --kubernetes-version=v1.16.1
```

Delete all of the minikube clusters:

```shell
minikube delete --all
```

For further interaction with `kubectl` refer to: [[kubectl usage]]

