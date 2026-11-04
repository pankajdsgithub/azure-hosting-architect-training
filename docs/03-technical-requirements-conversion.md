# 03. Business Requirement to Technical Requirements

This is the stage where business intent becomes technical architecture decisions.

## Conversion model

Business requirement -> functional requirement -> technical requirement -> Azure service mapping

### Example

Business need:

> Customer should be able to manage orders reliably during peak periods.

Functional requirement:

> The system must allow customers to retrieve and update order details securely.

Technical requirement:

> The platform must provide a public-facing API layer, stateless application services, secure identity integration, and autoscaling support.

Azure mapping:

- Azure API Management for API exposure and policy enforcement
- Azure Container Apps or AKS for stateless workloads
- Azure Key Vault for secrets and certificates
- Azure Front Door / Application Gateway for ingress and WAF
- Azure Monitor and Application Insights for telemetry

## Example conversion table

| Business need | FR | NFR | Technical requirement |
|---|---|---|---|
| Secure customer access | Users sign in securely | MFA recommended | Entra ID + conditional access |
| Reliable order service | Orders can be viewed and updated | 99.9% availability | Redundant services + health probes |
| Seasonal scale | System handles peak traffic | Auto-scale to 5x | Autoscale rules, queue decoupling |
| Compliance | Access logs kept | 90 day retention | Log analytics + retention policy |
| Cost control | Solution must be efficient | Right-size workloads | Use platform-managed services |

## Key technical design questions

- Which components are user-facing vs internal-only?
- What is the ingress and egress design?
- What security boundary is required?
- What data stores are needed?
- What integration patterns are required?
- How is resiliency handled?
- What is the alerting and support model?

## Typical technical requirements to define

### Identity and access

- Authentication model
- Authorization model
- Role-based access
- Secrets management
- Network restrictions

### Application hosting

- Web front end
- API gateway
- Backend services
- Background processing and event handling

### Data and integration

- Database type
- Data residency needs
- Messaging and async processing
- Integration with external systems

### Observability

- Logging strategy
- Metrics and alerting
- Traceability across requests
- Health, availability, and SLA monitoring

### Platform operations

- CI/CD workflow
- environment strategy
- deployment model
- rollback strategy

## Good architecture output

The technical requirement phase should produce a clear set of design decisions, such as:

- public vs private access model
- network topology
- identity foundation
- application hosting choices
- data platform choices
- security zones and controls
- operational responsibilities

This becomes the baseline for landing zone and HLD documentation.
