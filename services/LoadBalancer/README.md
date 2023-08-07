# k8s


```
kubectl apply -f nginx-service.yaml -n service-test
```

```
kubectl apply -f nginx-deployment.yaml -n service-test
```

```
kubectl describe services nginx-service -n service-test  
```

```
curl http://192.168.49.2:30493
```