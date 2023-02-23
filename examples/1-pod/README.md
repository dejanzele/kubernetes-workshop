# Pod

## What is a pod?

A Kubernetes Pod is the smallest deployable unit in Kubernetes, and represents a single instance of a running process in your cluster.

Pods can contain one or more containers, which share the same network namespace
and can communicate with each other using local inter-process communication (IPC) mechanisms.

Pods are usually used to run a single primary container along with sidecar containers that provide supporting functionality,
such as logging or monitoring.

Pods are ephemeral, which means they can be created, destroyed, and replaced dynamically in response to changes in your application or cluster.
Pods are also often created and managed by higher-level abstractions such as Deployments or StatefulSets,
which ensure that the desired number of replicas of your application are running at all times.

## Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: alpine-pod
spec:
  containers:
    - name: alpine
      image: alpine
      command: ["tail", "-f", "/dev/null"]
```

* `apiVersion`: This specifies the Kubernetes API version that the YAML file uses. In this case, we're using v1.
* `kind`: This specifies the type of Kubernetes object that we're creating. In this case, we're creating a pod.
* `metadata`: This is where we can provide metadata about the pod, such as the name.
* `spec`: This is where we define the specifications for the pod.
* `containers`: This is where we define the containers that will run within the pod. In this case, we're only defining one container named alpine.
* `name`: This specifies the name of the container.
* `image`: This specifies the Docker image that the container will use. In this case, we're using the alpine image.
* `command`: This specifies the command that the container will run. In this case, we're running tail -f /dev/null, which is a commonly used command to keep a container running in the background.

### Install

Run the following command to create the pod:
```bash
kubectl apply -f pod.yaml
```

### List

Run the following command to check the status of the Pod:
```bash
kubectl get pods
```

### Exec into Pod

Run the following command to exec into the Pod:
```bash
kubectl exec -it alpine-pod -- sh
```

### Delete

Run the following command to delete the Pod:
```bash
kubectl delete -f pod.yaml
```