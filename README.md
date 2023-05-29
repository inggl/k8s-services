# Kubernetes

## Requirements
- Kubectl
- Kind or Minikube
- Helm
- Docker

## Kind
<https://kind.sigs.k8s.io/>

## Minikube
Start
```shell
minikube start
````

Status
```shell
minikube status
```

Stop
```shell
minikube stop
```

Ingress
```shell
minikube addons enable ingress
```

Dashboard
```shell
minikube dashboard
```

### Tunnel
Service of type *NodePort* can be exposed via
```
minikube service <service-name> --url
```

Service of type *LoadBalancer* can be exposed via
```shell
minikube tunnel --cleanup
```

Delete
```shell
minikube delete --all --purge
```

## Kubectl
Version
```shell
kubectl version
```

Cluster
```shell
kubectl cluster-info
```

List all services in the namespace
```shell
kubectl get services
```

List all pods in the namespace
```shell
kubectl get pods
```

## Ingress
```shell
kubectl apply -f ingress.yaml
```

```shell
kubectl get ingress
```

## Helm
<https://helm.sh/>

### Artifact Hub
<https://artifacthub.io/>

List
```shell
helm list
```

## Services
### Traefik
Add *Traefik* *Helm* repository
```shell
helm repo add traefik https://helm.traefik.io/traefik && helm repo update
```

Install
```shell
helm install --create-namespace -n traefik traefik traefik/traefik --values=./traefik/values.yaml
```

Delete
```shell
kubectl delete namespace traefik
```

### Portainer
Add *Portainer* *Helm* repository
```shell
helm repo add portainer https://portainer.github.io/k8s/ && helm repo update
```

Install
```shell
helm install --create-namespace -n portainer portainer portainer/portainer
```

Expose
```shell
minikube service portainer -n portainer --url
```

Delete
```shell
kubectl delete namespace portainer
```