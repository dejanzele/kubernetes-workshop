# Namespace

## What is a Namespace?

Kubernetes Namespace is a way to logically divide your cluster into virtual sub-clusters.
It provides a scope for Kubernetes resources and helps to organize them into distinct groups.

Namespaces enable multiple teams or users to share a cluster while keeping their resources isolated from each other.
Each Namespace has its own set of Kubernetes resources, such as pods, services, and deployments.

## Example

```yaml
kind: Namespace
apiVersion: v1
metadata:
  name: test
  labels:
    tier: k8s-workshop
```

### Install

Run the following command to create the ConfigMap:
```bash
kubectl apply -f namespace.yaml
```

### Delete

Run the following command to delete the ConfigMap:
```bash
kubectl delete -f namespace.yaml
```