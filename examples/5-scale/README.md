# Deployment Scaling

## Example

### How to scale

Update the `.spec.replicas` field in the Deployment by either:
1. updating the deployment YAML and applying it using `kubectl`
2. using `kubectl scale --replicas=3 deployment/my-example`
3. using `kubectl edit deployment/my-example` and changing the value of `.spec.replicas`
