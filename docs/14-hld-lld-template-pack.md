# 14. HLD / LLD Template Pack

## 1. Purpose

This section provides a ready-to-use Word-style architecture document template pack for client-facing design documentation.

## 2. How to Use This Pack

Use the following templates in sequence:

1. High-Level Design (HLD)
2. Low-Level Design (LLD)
3. Architecture Decision Record (ADR)

The HLD explains the solution at a business and platform level, while the LLD goes into implementation-level details for engineering teams and review boards.

## 3. Recommended Document Structure

### HLD Document Outline

- Document control
- Executive summary
- Business context and requirements
- Current-state assessment
- Target-state architecture
- Logical architecture overview
- Technology selection summary
- Security architecture
- Networking and connectivity
- Availability, resiliency, and DR
- Monitoring and operations
- Cost and trade-offs
- Risks and assumptions
- Decision log and sign-off

### LLD Document Outline

- Document control
- Purpose and scope
- Asset inventory
- Detailed network design
- Detailed application design
- Data architecture
- Integration design
- Security controls
- HA/DR design
- Deployment design
- Monitoring and alerting
- Operational runbook
- Test strategy
- Risks and limitations
- Implementation checklist

### ADR Outline

- title
- status
- context
- decision
- alternatives
- rationale
- consequences
- impact analysis
- follow-up actions

## 4. Client-Ready Design Language

Use language like:

- The solution is designed to meet the stated business objective while balancing security, resilience, and cost.
- The architecture is based on the agreed functional and non-functional requirements.
- The selected service model minimizes operational overhead while maintaining compliance and supportability.
- The design preserves separation of concerns across ingress, application, data, and operations layers.

## 5. Template Files

- [templates/hld-template.md](../templates/hld-template.md)
- [templates/lld-template.md](../templates/lld-template.md)
- [templates/adr-template.md](../templates/adr-template.md)

## 6. Example Usage Flow

```text
Requirements -> HLD -> LLD -> ADR -> Review -> Approval
```

## 7. Practical Notes

- Keep the HLD brief but clear for leadership and stakeholder reviews.
- Keep the LLD detailed and implementation-focused for engineering and operations.
- Each major decision should be backed by a traceable requirement.
- Every design should identify assumptions, limitations, and follow-up actions.

## 8. Quick Revision Points

- HLD = what and why
- LLD = how and where
- ADR = decision rationale
- Architecture documentation is not optional; it is part of delivery quality

This pack is intended for enterprise design reviews, technical design documents, client proposal responses, and interview preparation.
