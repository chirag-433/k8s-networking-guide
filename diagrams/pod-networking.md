## Pod Networking Diagram

```mermaid
graph LR
    PodA["Pod A (10.0.1.5)"] <---> PodB["Pod B (10.0.2.7)"]
    CNI["CNI Plugin (Cilium/Calico/Flannel)"]
    PodA --- CNI
    PodB --- CNI
```

