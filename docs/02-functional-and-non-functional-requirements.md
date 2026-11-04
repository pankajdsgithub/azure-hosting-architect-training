# 02. Functional and Non-Functional Requirements

Requirements are the bridge between business intent and technical design.

## Functional requirements (FR)

Functional requirements describe what the system must do.

### Examples

- Users must be able to sign in securely.
- Customers must be able to view order status.
- The platform must allow API calls to backend services.
- The system must process payment confirmation events.
- A support dashboard must show service health and key KPIs.
- The platform must support role-based access for administrators.

### FR writing pattern

Use the format:

- Actor
- Action
- Outcome
- Constraint

Example:

> As a customer, I must be able to view my order status in real time so that I can track fulfillment.

## Non-functional requirements (NFR)

Non-functional requirements describe how the system should behave under different conditions.

### Common NFR categories

- Availability
- Scalability
- Performance
- Security
- Reliability
- Recoverability
- Maintainability
- Observability
- Compliance
- Cost efficiency

### Examples

- The platform must provide 99.9% availability for customer-facing APIs.
- User login requests must respond within 2 seconds at the p95 level.
- The system must support seasonal traffic spikes up to 5x baseline.
- Data in transit must be encrypted using TLS 1.2 or higher.
- The platform must support rollback to previous version within 30 minutes.
- Operational logs must be retained for at least 90 days.

## Example FR/NFR matrix

| Area | Requirement type | Requirement |
|---|---|---|
| Customer access | FR | Customer can view orders |
| API access | FR | System exposes product and order APIs |
| Performance | NFR | p95 API latency under 2 seconds |
| Availability | NFR | 99.9% uptime for customer services |
| Security | NFR | MFA for admin access |
| Scalability | NFR | 5x autoscaling during peak demand |
| Recovery | NFR | Restore service within 30 minutes |
| Compliance | NFR | Logs retained and auditable |

## Good requirement characteristics

- Clear and testable
- Realistic and measurable
- Traceable to a business need
- Not written as a design decision too early
- Not overly vague

## Common mistake

Do not write a requirement as a solution. For example:

- Bad: "Use AKS with ingress controller"
- Better: "The platform must support secure, scalable, HTTP-based access for production workloads"

## Output of this phase

The result is a structured list of FR and NFR statements that can be mapped to:

- Azure services
- network design
- security model
- operations model
- cost and reliability strategy

This becomes the foundation for the technical design phase.
