## Service Load Balancing Diagram

```mermaid
graph LR
    User --> Service["Kubernetes Service"]
    Service --> Pod1["Pod 1"]
    Service --> Pod2["Pod 2"]
    Service --> Pod3["Pod 3"]
```

