# Kubernetes Networking Basics

Kubernetes networking allows containers running inside pods to communicate with each other reliably across a cluster. The goal is to make networking simple and consistent regardless of where pods are scheduled.

## Key Principles

- Every pod gets its own IP address.
- Pods can communicate directly without NAT inside the cluster.
- Networking is implemented using a CNI (Container Network Interface) plugin such as Cilium, Calico, or Flannel.

## Pod Communication

When a pod is created, Kubernetes assigns it an IP address. Other pods can communicate directly using this IP. This creates a flat network model where pods behave similarly to machines on the same network.

## Role of CNI Plugins

CNI plugins handle:

- IP allocation
- Routing between pods
- Network security enforcement
- Observability and monitoring (in advanced CNIs like Cilium)

Understanding Kubernetes networking fundamentals helps in debugging connectivity issues and designing reliable cloud-native applications.
