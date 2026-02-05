## External Load Balancing Diagram

```mermaid
graph LR
    Internet --> Ingress["Ingress / LoadBalancer"]
    Ingress --> Service
    Service --> Pod1
    Service --> Pod2
```

