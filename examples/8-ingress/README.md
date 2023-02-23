# Ingress

An Ingress is an API object that defines rules which allow external access to services in a cluster.
An Ingress controller fulfills the rules set in the Ingress.
An Ingress serves as an L7 Load Balancer.

## Example

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: k8s-workshop-example
spec:
  ingressClassName: nginx
  rules:
    - host: example.bakson.rs
      http:
        paths:
          - path: /health
            pathType: Prefix
            backend:
              service:
                name: k8s-workshop-example
                port:
                  number: 8080
```

* `kind` field specifies that this is an Ingress resource, which is used to expose HTTP(S) routes from outside the cluster to services within the cluster.
* `metadata` section provides information about the Ingress, including its name (k8s-workshop-example).
* `spec` section defines the specification for the Ingress, which includes the ingressClassName field set to nginx, indicating that this Ingress should be handled by the Nginx ingress controller.
* `rules` section specifies a rule for routing traffic based on the incoming host. In this case, the rule specifies that requests for example.bakson.rs should be routed to this Ingress.
* `http` section within the rule specifies that the Ingress should handle HTTP requests.
* `paths` section lists the different paths that this Ingress should handle. In this case, it specifies one path: /health.
* `pathType` field set to Prefix means that requests with paths that start with /health should be handled by this Ingress.
* `backend` section specifies the Kubernetes Service that should receive traffic for this path. The service field specifies the name of the service, which is k8s-workshop-example, and the port field specifies the port number of the service that should receive traffic, which is 8080.

### Exposing the app

We want to expose the application now to the outside world.

There are 2 ways to do it:
1. either expose the Service as a NodePort or LoadBalancer
2. use an Ingress controller and expose the Controller and access our app through it

We will opt for the second option and now we need to install an Ingress controller.

Let's install NGINX Ingress controller as a Minikube addon:

```bash
minikube addons enable ingress -p k8s-workshop
```

Now let's open a tunnel to our Ingress controller:

```bash
minikube tunnel -p k8s-workshop
```