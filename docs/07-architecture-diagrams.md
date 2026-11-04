# 07. Architecture Diagrams

Diagrams are a critical communication tool for architecture reviews and stakeholder alignment.

## 1. Logical architecture flow

```mermaid
flowchart LR
    User[End User] -->|HTTPS| FrontDoor[Azure Front Door / WAF]
    FrontDoor --> APIM[API Management]
    APIM --> App[Application Services]
    App --> SQL[(Azure SQL)]
    App --> Cache[(Redis)]
    App --> SB[Service Bus]
    SB --> Worker[Background Worker]
    App --> AI[Application Insights]
    APIM --> Monitor[Azure Monitor]
```

## 2. Landing zone reference diagram

```mermaid
flowchart TB
    subgraph Tenant[Azure Tenant]
        subgraph MG[Management Group]
            Platform[Platform Services]
            Prod[Production Subscription]
            NonProd[Non-Production Subscription]
        end
    end

    Platform --> Identity[Microsoft Entra ID]
    Platform --> Monitor[Azure Monitor]
    Platform --> Policy[Azure Policy]
    Prod --> Workloads[Workloads]
    NonProd --> Dev[Dev/Test Workloads]
```

## 3. Security and network view

```mermaid
flowchart TD
    Internet[Internet] --> Edge[Public Edge Tier]
    Edge --> WAF[WAF / Firewall]
    WAF --> APIM[API Management]
    APIM --> AppSubnet[Application Subnet]
    AppSubnet --> DB[Private Data Services]
    AppSubnet --> KV[Key Vault]
    DB --> Logs[Monitoring / Logs]
    AppSubnet --> Id[Managed Identity]
```

## 4. Event-driven processing pattern

```mermaid
sequenceDiagram
    participant C as Client
    participant API as Application API
    participant SB as Service Bus
    participant W as Worker
    participant DB as Database

    C->>API: Create order / event trigger
    API->>DB: Save order status
    API->>SB: Publish event
    SB->>W: Deliver message
    W->>DB: Update downstream processing
    W-->>API: Status acknowledgement
```

## Tips for architecture diagrams

- Keep the diagram readable for non-technical stakeholders
- Show major trust boundaries and security zones
- Highlight external dependencies and core integration points
- Separate ingress, application, data, and operations layers
- Use consistent naming and labels across diagrams
