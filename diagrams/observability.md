## Observability Diagram

```mermaid
graph LR
    Pod --> Service
    Service --> Monitor["Monitoring / Logs / Metrics"]
    Monitor --> User
```

