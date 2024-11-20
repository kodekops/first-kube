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

We have created a deployment with two replicas, but we cannot access those
instances from outside the cluster. We need to create a service to expose the
pod to the outside world.

We can run the following command to create a service:

```bash
kubectl expose deployment my-app --type=NodePort --port 8080 --target-port 8080
```
