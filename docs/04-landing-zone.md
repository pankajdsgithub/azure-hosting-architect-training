# 04. Landing Zone Design

A landing zone is the foundational platform that makes workloads secure, governable, and operable at scale.

## Landing zone goals

- Standardize network and identity design
- Enforce security and governance policies
- Support multi-environment deployment
- Enable repeatable application delivery
- Reduce operational drift and risk

## Core design zones

### Management group and governance layer

- hierarchy for production, shared, and platform subscriptions
- policy enforcement
- cost management and tagging
- RBAC boundaries

### Identity and access foundation

- Microsoft Entra ID
- managed identity for workload authentication
- role separation between platform and workload teams
- conditional access and MFA for admin operations

### Network foundation

- hub-and-spoke or virtual WAN topology
- segmentation between internet, application, data, and management tiers
- private endpoints for data services
- firewall and routing controls
- restricted egress and ingress policies

### Security foundation

- Defender for Cloud
- Key Vault for secrets and certificates
- managed disks and encryption defaults
- vulnerability scanning and compliance baseline
- centralized logging and SIEM integration

### Monitoring and operations

- Log Analytics / Azure Monitor
- Application Insights
- alert rules and dashboards
- health checks and platform uptime reporting

## Example landing zone structure

```text
Azure Tenant
└── Management Groups
    ├── Platform
    │   ├── Identity
    │   ├── Connectivity
    │   └── Management
    ├── Production
    │   ├── Shared Services
    │   ├── App Tier
    │   └── Data Tier
    └── Non-Production
        ├── Dev
        ├── Test
        └── UAT
```

## Landing zone design considerations

- Use separate subscriptions for prod and non-prod
- Separate management and workload responsibilities
- Ensure all resources are tagged with owner, env, cost center, and compliance metadata
- Standardize naming, networking, and security baselines
- Include a shared services layer for DNS, monitoring, and identity

## Example enterprise landing zone policy goals

- No public access to critical data services by default
- All secrets stored in Key Vault
- Resource locks on core platform components
- Environment isolation by subscription or resource group
- Mandatory tagging and diagnostic settings

## Outcome

A landing zone enables the platform team to provide secure, repeatable, and scalable foundations for application workloads. It is the environment in which HLD and LLD are then implemented.
