# Azure Hosting Architect Training Repository

This repository is a complete training and reference package for Azure hosting architecture work. It is designed for architecture interviews, technical design discussions, and hands-on learning around translating business requirements into an Azure-native solution.

## What is included

- Business requirement discovery questions
- Functional and non-functional requirements
- Conversion from business needs to technical requirements
- Landing zone design guidance
- High-level design (HLD)
- Low-level design (LLD)
- Architecture diagrams
- Interview-style architecture questions
- Design decision rationale

## Repository structure

```text
.
├── README.md
├── docs/
│   ├── 00-index.md
│   ├── 01-business-requirement-discovery.md
│   ├── 02-functional-and-non-functional-requirements.md
│   ├── 03-technical-requirements-conversion.md
│   ├── 04-landing-zone.md
│   ├── 05-hld.md
│   ├── 06-lld.md
│   ├── 07-architecture-diagrams.md
│   └── 08-interview-questions.md
└── diagrams/
    └── README.md
```

## Suggested learning flow

1. Start with business discovery questions.
2. Convert the business context into FR/NFRs.
3. Translate those into technical requirements.
4. Design the landing zone and shared platform foundations.
5. Build HLD and LLD.
6. Validate with architecture diagrams and interview questions.

## Typical architecture scenario

This repo is aligned to a common enterprise scenario:

- multi-tier application platform
- secure internet-facing and internal workloads
- Azure-native landing zone
- ingress through APIM / Application Gateway / Front Door
- backend APIs and data services
- telemetry, observability, governance, and security controls

## Core design themes

- Security by default
- Least privilege access
- Scalability and resilience
- High availability and disaster recovery
- egress and networking control
- Platform operations readiness
- Cost awareness and governance
- Compliance and auditability

## Useful references

- Azure Well-Architected Framework
- Azure landing zone design guidance
- Azure enterprise-scale reference architecture
- Microsoft Cloud Adoption Framework

---

This repository is intended to help practice and present architecture thinking in a structured, business-aware way.
