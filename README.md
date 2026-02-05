# k8s-networking-guide

This is a beginner-friendly documentation project that explains Kubernetes networking concepts such as services, load balancing, network security, and observability. The goal is to make cloud-native networking easier to understand through clear explanations, practical examples, and simple diagrams.

## Kubernetes Networking — A Beginner Guide

Kubernetes networking can feel confusing at first because many things happen automatically behind the scenes. This guide breaks down the basics so you can understand how communication works inside a Kubernetes cluster.

**We’ll focus on:**

- Pod networking fundamentals  
- Kubernetes Services  
- Load balancing concepts  
- Network security basics  
- Observability and troubleshooting  

---

## Pods Networking Basics

### What is a Pod?

A pod is the smallest deployable unit in Kubernetes. Most of the time, it contains a single container, although sometimes multiple tightly connected containers run together.

Each pod gets:

- Its own IP address inside the cluster  
- A shared network environment between its containers  

You can think of a pod as a tiny machine with its own network identity.

### How Pods Communicate

One of Kubernetes’ core networking principles is simple:

> Any pod should be able to talk to any other pod directly.

This works because Kubernetes uses a Container Network Interface (CNI) plugin like Cilium, Calico, or Flannel to handle networking automatically.

For example:

- Pod A → `10.0.1.5`  
- Pod B → `10.0.2.7`  

Pod A can directly send a request to Pod B without manual routing or port mapping.

### Key Points to Remember

- Every pod has its own IP.  
- Pods communicate directly across the cluster.  
- The networking setup is managed by a CNI plugin.  

---

## Kubernetes Services

### Why Services Are Needed

Pods don’t last forever:

- They restart  
- They move between nodes  
- Their IPs change  

If your application relied on pod IPs directly, it would break constantly. Services solve this by giving you a stable endpoint.

### What a Service Does

A Kubernetes Service:

- Groups pods using labels (like `app=backend`)  
- Provides a stable virtual IP (ClusterIP)  
- Creates a DNS name inside the cluster  
- Automatically distributes traffic across pods  

So instead of calling individual pod IPs, apps simply call:

```text
http://backend
```

And Kubernetes routes traffic to the right pods.

### Common Service Types

- **ClusterIP**  
  Used inside the cluster only. This is the default type.

- **NodePort**  
  Exposes the service on every node using a fixed port.

- **LoadBalancer**  
  Creates an external load balancer in cloud environments so outside users can access your app.

---

## Load Balancing in Kubernetes

Load balancing happens at multiple levels.

### Inside the Cluster

Services distribute traffic across pods automatically. You usually don’t need to configure anything manually.

### Outside the Cluster

Typical cloud setup:

- External Load Balancer  
- Kubernetes Node  
- Service  
- Pods  

Often an **Ingress Controller** (like NGINX or Traefik) handles advanced routing such as:

- Multiple domains  
- Path-based routing  
- TLS termination  

---

## Network Security Basics

By default, many Kubernetes clusters allow pods to communicate freely. While convenient, this isn’t ideal for production environments.

### NetworkPolicies

NetworkPolicies let you control:

- Which pods can receive traffic  
- Which pods can send traffic  
- Communication rules based on labels  

For example:

- Allow frontend → backend traffic  
- Block everything else  
- Allow only necessary external access  

This approach improves security and helps move toward a zero-trust network model.

---

## Observability: Understanding What’s Happening

Networking issues are common when learning Kubernetes. Observability helps you see what’s going on.

### Useful kubectl Commands

Check pods and IPs:

```bash
kubectl get pods -o wide
```

Check services:

```bash
kubectl get svc
```

Check endpoints:

```bash
kubectl get endpoints
```

These commands quickly show whether networking is configured correctly.

### Debug Pods

You can launch a temporary debug container:

```bash
kubectl run net-debug --image=nicolaka/netshoot -it --rm -- sh
```

From inside it you can:

- Ping services  
- Test DNS  
- Send HTTP requests  

This is often the fastest way to troubleshoot.

---

## Final Thoughts

Kubernetes networking may seem complex initially, but the core ideas are straightforward:

- Pods get their own IPs.  
- Services provide stable access to pods.  
- Load balancing happens automatically.  
- NetworkPolicies improve security.  
- Observability tools help you debug and understand traffic.  

Once you understand these basics, tools like Cilium become much easier to explore.

---

## Why I Made This

I created this guide to better understand Kubernetes networking myself while practicing technical documentation and concept explanation. I hope it helps other beginners navigate cloud-native networking more confidently.

## Documentation

Detailed documentation is available in the `/docs` folder:

- Networking fundamentals
- Kubernetes Services
- Network security basics

