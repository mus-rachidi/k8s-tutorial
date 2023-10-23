# Intro Helm

Helm is a package manager and application management tool for Kubernetes that packages multiple Kubernetes resources into a single logical deployment unit called a Chart.

## prerequisite

1. Helm
2. Minikube 
3. kubectl

## Create cluster using minikube

```
minikube start --nodes 1 --profile minikube --driver=docker
```

## Install Helm CLI

```
curl -sSL https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```
We can verify the version

```
helm version --short
```
## Deploy Nginx using Helm

```
helm repo add bitnami https://charts.bitnami.com/bitnami
```

```
helm repo update
```
## use Helm to deploy the bitnami/nginx chart

```
helm install mywebserver bitnami/nginx
```

## In order to review the underlying Kubernetes services, pods and deployments, run:

```
kubectl get all 
```

```
kubectl get service  
NAME                TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
kubernetes          ClusterIP      10.96.0.1       <none>        443/TCP        13m
mywebserver-nginx   LoadBalancer   10.98.170.225   <pending>     80:32044/TCP   10m

```
## Check if work

1. inside minikube 

Log into the minikube environment using

```
minikube ssh 
```

```
curl 10.98.170.225
```
2. using web browser 

Copy the value for minikube ip, 

```
minikube ip   
192.168.67.2
```
open a new tab in your web browser, and paste it in with the port of service 

http://192.168.67.2:32044/