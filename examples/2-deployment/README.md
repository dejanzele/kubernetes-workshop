# Deployment

## What is a Deployment?

A Kubernetes Deployment is a higher-level abstraction that allows you to manage and update multiple instances (replicas)
of a pod or containerized application.
Instead of creating and managing individual pods manually, you can use a Deployment to manage them as a group.

A Deployment ensures that a specified number of replicas are running at all times,
and can automatically scale the number of replicas up or down based on demand.
This makes it easier to ensure that your application can handle increasing traffic and usage without overloading or crashing.

Deployments also make it easy to roll out new versions of your application,
by gradually updating the replicas one at a time, to avoid downtime or service disruption.

Additionally, Deployments can automatically roll back to a previous version of the application if an update causes issues,
helping you maintain the stability and reliability of your application.

## Example

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: k8s-workshop-example
spec:
  replicas: 1
  selector:
    matchLabels:
      app: example
  template:
    metadata:
      labels:
        app: example
    spec:
      containers:
        - name: app
          image: dpejcev/testkube-triggers-example:1.0.15
          ports:
            - containerPort: 8080
```


* `apiVersion`: This specifies the Kubernetes API version that the YAML file uses. In this case, we're using the apps/v1 API version.
* `kind`: This specifies the type of Kubernetes object that we're creating. In this case, we're creating a Deployment.
* `metadata`: This is where we can provide metadata about the Deployment, such as the name.
* `spec`: This is where we define the specifications for the Deployment.
* `replicas`: This specifies the desired number of replicas of the application that should be running at any given time. In this case, we're specifying 1 replica.
* `selector`: This specifies how Kubernetes should select which pods to manage with this Deployment. In this case, we're using a label selector to match pods with the label app: example.
* `matchLabels`: This specifies the label selector that Kubernetes should use to select pods.
* `template`: This specifies the pod template that Kubernetes should use to create new pods managed by this Deployment.
* `labels`: This specifies the labels that should be applied to the pods created from this template. In this case, we're applying the label app: example.
* `containers`: This specifies the containers that should run within the pods created from this template.
* `name`: This specifies the name of the container.
* `image`: This specifies the Docker image that the container will use. In this case, we're using the dpejcev/testkube-triggers-example image with the version 1.0.15.
* `ports`: This specifies the ports that should be exposed by the container. In this case, we're exposing port 8080.

### Install

Run the following command to create the Deployment:
```bash
kubectl apply -f deployment.yaml
```

### List

Run the following command to check the status of the Deployment:
```bash
kubectl get deployments
```

### Describe

Run the following command to check the details of the Deployment:
```bash
kubectl describe deployment k8s-workshop-example
```

### Logs

Run the following command to check the logs of the Deployment:
```bash
kubectl logs deployment/k8s-workshop-example
```

### Delete

Run the following command to delete the Deployment:
```bash
kubectl delete -f deployment.yaml
```