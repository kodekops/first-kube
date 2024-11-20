# Deployment in Kubernetes

We can use deployment in Kubernetes to deploy the application. We can create
a deployment using the following command:

```bash
kubectl create deployment my-app --image kodega2016/first-kube --port 80
--replicas 2
```

We can check the deployment using the following command:

```bash
kubectl get deployments
```

It will list all the deployments in the cluster.

We can get more information about the deployment using the following command:

```bash
kubectl describe deployment my-app
```
