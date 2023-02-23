# Service

## What is a Service?

A Kubernetes Service is an abstraction that provides a stable IP address and DNS name for a set of Pods,
allowing other parts of your application to access them consistently.

Services act as a load balancer and proxy, distributing traffic to the correct Pods based on labels that you define.

Services are used to decouple the network topology of your application from its actual implementation,
making it easier to scale and update your application without disrupting its external interfaces.

Services can be created for different types of traffic, such as HTTP, TCP, or UDP,
and can be configured with different load balancing algorithms and session affinity options.

Services can also provide service discovery and load balancing for external services,
such as databases or APIs that are not part of your Kubernetes cluster.

## Example

```yaml
apiVersion: v1
kind: Service
metadata:
  name: k8s-workshop-example
spec:
  selector:
    app: example
  ports:
    - name: http
      port: 8080
      targetPort: 8080
  type: ClusterIP
```