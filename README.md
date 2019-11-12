# Service Account

```
kubectl apply -f ./service_account/admin.yaml
```

# Cluster Role

```
kubectl apply -f ./cluster_role/admin.yaml
```

# Get Token

```
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
```

# Proxy (Only Local)

```
kubectl proxy
```

# K8S Dashbaord

http://127.0.0.1:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard
