## Network Policy Diagram

```mermaid
graph LR
    Frontend["Frontend Pod"] --> Backend["Backend Pod"]
    Unknown["Unknown Pod"] -. Blocked .-> Backend
```

