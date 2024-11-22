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

Now we can access the application using the following URL:

```bash
minikube service my-app
```

We can also scale the deployment using the following command:

```bash
kubectl scale deployment/my-app --replicas=4
```

We can update the deployment using the following command:

```bash
kubectl set image deployment/my-app my-app=kodega2016/first-kube:v2
```

We can view the deployment history using the following command:

```bash
kubectl rollout history deployment/my-app
```

To view the status of the deployment, we can use the following command:

```bash
kubectl rollout status deployment/my-app
```

We can view the roll out details using the following command:

```bash
kubectl rollout history deployment/my-app --revision=2
```

To rollback the deployment, we can use the following command:

```bash
kubectl roolout undo deployment/my-app
```

It will rollback to the previous version.

If we need to rollback to a specific version, we can use the following command:

```bash
kubectl roolout undo deployment/my-app --to-revision=2
```

That's it all using imperative commands. We can also use declarative way to
provision the deployment.

We have created deployment configuration inside the `k8s` folder.Now we can
apply the configuration using the following command:

```bash
kubectl apply -f k8s
```

To delete the resources

```bash
kubectl delete -f k8s
```

We can update the deployment configuration and apply the changes using the
same command.

```bash
kubectl apply -f k8s
```

## Liveness Probe

It determines when to restart a container,It check the health of the container.
If the liveness probe fails, the container will be restarted.

## Startup Probe

Sometimes,the container may take time to start. In such cases, we can use the
startup probe to determine when the container is ready.

If the startup probe fails, the container will be restarted.
