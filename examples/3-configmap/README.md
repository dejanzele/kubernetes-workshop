# ConfigMap

## What is a ConfigMap?

A Kubernetes ConfigMap is a key-value store that can be used to store configuration data and other non-sensitive information that your application needs.

ConfigMaps are decoupled from your application code,
allowing you to change configuration data without having to rebuild or redeploy your application.

ConfigMaps can be created from literal values or from files,
and can be consumed by your application as environment variables, command-line arguments, or configuration files.

ConfigMaps can also be updated dynamically and used to configure multiple parts of your application simultaneously.

## Example

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: testkube-triggers-example-config
  namespace: testkube
data:
  config.yaml: |
    crash: false
    slow: false
```

### Install

Run the following command to create the ConfigMap:
```bash
kubectl apply -f configmap.yaml
```

### List

Run the following command to check the status of the ConfigMap:
```bash
kubectl get configmap
```

### Describe

Run the following command to check the details of the ConfigMap:
```bash
kubectl describe configmap k8s-workshop-example-config
```

### Delete

Run the following command to delete the ConfigMap:
```bash
kubectl delete -f configmap.yaml
```