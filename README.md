# Kubernetes

## Requirements
- Kubectl
- Kind or Minikube
- Helm
- Docker
- VirtualBox

## Installation
### Kubectl
#### Environment variable
Add *kubectl* to environment variable

```shell
kubectl version
```

```shell
kubectl cluster-info
```

```shell
kubectl get srv -A
```

### Kind
<https://kind.sigs.k8s.io/>

### Minikube
#### Environment variable
Add *minikube* to environment variable

#### Setup default driver
```shell
minikube config set driver docker
```

```shell
minikube config set driver hyperv
```

or

```shell
minikube start --driver=docker --memory 4000
````

```shell
minikube start --driver=virtualbox --memory 4000
````

```shell
minikube start --driver=hyperv --memory 4000
```

#### Memory limit
```shell
minikube config set memory 2048m
```

#### Status
```shell
minikube status
```

#### Stop
```shell
minikube stop
```

#### Delete
```shell
minikube delete --all --purge
```

#### Ingress
NGINX ingress
```shell
minikube addons enable ingress
```

Traefik \
Install Traefik using Helm Traefik Chart


#### Dashboard
```shell
minikube dashboard
```

### Commands
#### Create container
```
kubectl run <container_name> --image=<image>
```

#### Expose container
```
kubectl expose pod <container_name> --type=NodePort --port=8080
```

#### Access container
```
minikube service <container_name> --url
```

#### Delete
```
kubectl delete pods <container_name>
```

```
kubectl delete service <container_name>
```

#### Ingress
```shell
kubectl apply -f ingress.yaml
```

```shell
kubectl get ingress
```

### Helm
<https://helm.sh/>

Add *helm* to environment variable

#### Artifact Hub
<https://artifacthub.io/>

#### Building Chart
```
helm create <chart-name>
```

#### Default values
Pass default values into *values.yaml*

#### Charts file
*Charts.yaml* contains the information about the Chart as name, version and description.

#### Package
```
helm package <chart-name>
```

#### Install local Helm Chart
```
helm install <release-name> <chart-name>-<version>.tgz
```

#### List
```shell
helm list
```

#### Delete
```
helm uninstall <release_name>
```

### Services
#### Traefik
##### Install
```shell
kubectl create namespace traefik
```

```shell
helm repo add traefik https://helm.traefik.io/traefik
```

```shell
helm repo update
```

```shell
helm install traefik traefik/traefik --values=./traefik/values.yaml
```

#### NGINX
```shell
kubectl create namespace nginx
```

```shell
kubectl apply -f ./nginx/deployment.yaml
```