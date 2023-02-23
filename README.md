# Kubernetes Workshop
Welcome to my Kubernetes Workshop repository! This repository contains all the resources you need to get started with Kubernetes.

## What is Kubernetes?
Kubernetes is an open-source container orchestration system that automates the deployment, scaling, and management of containerized applications.
It is a popular tool used by many companies and is becoming an essential skill for developers and system administrators.

## Workshop Overview
This workshop is designed for beginners who have little to no experience with Kubernetes. In this workshop, you will learn:

1. What Kubernetes is and how it works
2. How to set up a Kubernetes cluster
3. How to deploy and manage applications on Kubernetes
4. How to scale and update applications on Kubernetes
5. Best practices for working with Kubernetes

## Workshop Structure
The workshop is divided into several sections, each covering a different aspect of Kubernetes. Each section contains a set of tutorials, examples, and exercises to help you learn and practice.

Here's a brief overview of the sections:

* Section 1: Introduction to Kubernetes: In this section, you will learn the basics of Kubernetes, including its architecture, components, and key concepts.
* Section 2: Setting up a Kubernetes Cluster: In this section, you will learn how to set up a Kubernetes cluster on your local machine or on a cloud provider like AWS or GCP.
* Section 3: Deploying Applications on Kubernetes: In this section, you will learn how to deploy applications on Kubernetes using Kubernetes manifests and Helm charts.
* Section 4: Managing Applications on Kubernetes: In this section, you will learn how to manage applications on Kubernetes, including scaling, updating, and rolling back.
* Section 5: Best Practices for Working with Kubernetes: In this section, you will learn best practices for working with Kubernetes, including security, monitoring, and troubleshooting.

## Getting Started
To get started with this workshop, simply clone this repository and follow the instructions in each section.
Each section contains a README file that explains what you need to do and provides links to relevant resources.

If you have any questions or issues, feel free to open an issue or reach out to the maintainers of this repository.

Happy learning!

### Prerequisites
You will need to install two tools in order to successfully follow this guide:
* [Docker Desktop](https://www.docker.com/products/docker-desktop/) - Docker Desktop is a one-click-install application for your Mac, Linux, or Windows environment that enables you to build and share containerized applications and microservices.
* [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) - The Kubernetes command-line tool, kubectl, allows you to run commands against Kubernetes clusters.
* [minikube](https://minikube.sigs.k8s.io/docs/start/) - minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.
* [helm](https://helm.sh/docs/intro/install/) - Helm is a package manager for Kubernetes that allows you to define, install, and upgrade Kubernetes applications.

### Setting up local Kubernetes cluster
For the purpose of this guide, we will use Kubernetes v1.24.9.

After installing the tools mentioned in the [Prerequisites](#prerequisites) section, run the following command:
```shell
minikube start --kubernetes-version=1.24.9 -p k8s-workshop
```

The output log should look something like this:
```
😄  [k8s-workshop] minikube v1.29.0 on Darwin 12.6 (arm64)
✨  Automatically selected the docker driver
📌  Using Docker Desktop driver with root privileges
👍  Starting control plane node k8s-workshop in cluster k8s-workshop
🚜  Pulling base image ...
🔥  Creating docker container (CPUs=2, Memory=4000MB) ...
🐳  Preparing Kubernetes v1.24.9 on Docker 20.10.23 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🔎  Verifying Kubernetes components...
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "k8s-workshop" cluster and "default" namespace by default
```

Now to check that `kubectl` is wired up correctly:
```shell
kubectl get nodes
```

The output should look like:
```
NAME           STATUS   ROLES           AGE   VERSION
k8s-workshop   Ready    control-plane   68s   v1.24.9
```

Now enable the minikube ingress addon:
```shell
minikube addons enable ingress -p k8s-workshop
```

## References
* [Kubernetes docs](https://kubernetes.io/docs/home/) - Official Kubernetes documentation
* [kubectl docs](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) - Official kubectl reference documentation
* [helm docs](https://helm.sh/docs/) - Official Helm documentation