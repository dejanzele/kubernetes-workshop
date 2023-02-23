# Helm

## What is Helm?

Helm is a package manager for Kubernetes that simplifies the deployment and management of complex applications on a Kubernetes cluster.

Helm uses templates called "charts" to define the components and configurations needed to deploy an application, including container images, volumes, environment variables, and more.

Using Helm, you can easily install, upgrade, and roll back applications on your cluster, as well as share your own applications with others through a central chart repository.

Helm also allows you to customize the configuration of an application by providing values files or using command-line arguments, making it easier to deploy applications in different environments.

## Example

### Install

Run the following command to install the Helm chart for the Example application:

```bash
helm install my-example ./example
```

### Uninstall

Run the following command to uninstall the Helm chart for the Example application:

```bash
helm uninstall my-example
```