## Running your first containers in Kubernetes

This guide will help you get oriented to Kubernetes and running your first containers on the cluster.

### Running a container (simple version)

From this point onwards, it is assumed that `kubectl` is on your path from one of the getting started guides.

The [`kubectl create`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#create) line below will create a [deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) named `demo-nginx` to ensure that there are always a [nginx](https://hub.docker.com/_/nginx/) [pod](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/) running.

```bash
kubectl create deployment --image nginx demo-nginx
```

You can list the pods to see what is up and running:

```bash
kubectl get pods
```

You can see whether demo-nginx is running or not using port-forward
The port 80 is nginx default port and we are forwarding the traffic to 8080.
Please replace the 'pod-name' with name retrieved using get pods command.

```bash
kubectl port-forward <pod-name> 8080:80
```

You can also see the deployment that was created:

```bash
kubectl get deployment
```

You can also scale the deployment to ensure there is two nginx pods running:

```bash
kubectl scale deployment --replicas 2 demo-nginx
```

You can now list the pods to see there is two up and running:

```bash
kubectl get pods
```

### Cleanup

To delete the two replicated containers, delete the deployment:

```bash
kubectl delete deployment demo-nginx
```

### Next: Configuration files

Most people will eventually want to use declarative configuration files for creating/modifying their applications.  A [simplified introduction](https://kubernetes.io/docs/user-journeys/users/application-developer/foundational/#section-2)
is given in a different document.


