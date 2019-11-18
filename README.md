# Dashboard

In order to access kubernetes dashboard you will need to completely the step below.

```
kubectl apply -f ./dashboard/ui.yaml

// create service account
kubectl apply -f ./service_account/admin.yaml
// or
kubectl apply -f ./service_account/admin_binding.yaml

// cluster role binding
kubectl apply -f ./cluster_role/admin.yaml
```

You can access kubernetes dashbaord via http://127.0.0.1:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy

## Get Token

```
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
```

## K8S Proxy (Only Local)

```
kubectl proxy
```

# GO Application

Under `/app/go` you will find `/k8s` directory where contains kubernetes and example simple HTTP golang apllication stuff. You can follows each steps to deploy go application to kubernetes in README.md
