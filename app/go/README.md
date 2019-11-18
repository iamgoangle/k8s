# Guideline GO + Containerize + K8S

#### Docker image

```
docker build -t goangle/go-app:v1.0.0 .
docker push goangle/go-app:tagname
```

#### Deployment

Create a new deployment.

```
kubectl apply -f ./k8s/deployment.yml
```

then you can test locally by

```
// port-forward
kubectl port-forward go-app-976f66f55-k25l4 8080 -n=kube-system
```

#### Service

Expose your service to network.

```
kubectl apply -f ./k8s/service.yml
```

#### Reference

- https://www.digitalocean.com/community/tutorials/how-to-deploy-resilient-go-app-digitalocean-kubernetes
- https://medium.com/google-cloud/deploy-go-application-to-kubernetes-in-30-seconds-ebff0f51d67b
