# 12. Real-World Enterprise Case Studies

## Case Study 1: On-Premises Application Modernization to Azure

### Business context

A manufacturing company wants to modernize a legacy on-prem application used by internal employees and plant managers.

### Discovery questions

- Is the app customer-facing or internal only?
- What are the outage cost and business criticality?
- Is SQL Server compatibility required?
- Do they need private connectivity to on-prem systems?

### Typical technical result

- Azure SQL Managed Instance or SQL Server VM
- App Service or AKS depending on modernization scope
- ExpressRoute or VPN to connect on-prem
- Azure Monitor and backup policies
- landing zone governance

### Final architecture decision

Modernize with a managed Azure app platform, private connectivity, and secure landing zone controls rather than a full redevelopment overhaul.

---

## Case Study 2: E-Commerce Application with Seasonal Peaks

### Business context

An e-commerce company sees large seasonal spikes and needs high availability plus cost-efficient autoscaling.

### Architecture choices

- Front Door and WAF for public ingress
- App Service or Container Apps for stateless services
- Redis for hot reads
- Azure SQL for transactional orders
- Service Bus for order processing and notifications

### Key concern

Peak demand without overprovisioning during normal periods.

---

## Case Study 3: High-Volume Event-Driven Platform

### Business context

A telecom or IoT platform ingests millions of events daily and needs stream analytics.

### Architecture choices

- Event Hubs or Kafka for ingestion
- consumer groups for multiple downstream processing systems
- storage and analytics layer for reporting
- monitoring for backlog and lag

### Key concern

Throughput, retention, replay, consumer lag, and cost control.

---

## Case Study 4: Multi-Client Azure Landing Zone

### Business context

A managed hosting provider supports multiple client workloads on Azure with strict isolation.

### Architecture choices

- management groups and subscription segmentation
- shared connectivity and identity layers
- per-client landing zones
- Azure Policy and RBAC enforcement
- separate production and non-production boundaries

### Key concern

Governance, isolation, and cost accountability.

---

## Case Study 5: Business-Critical Banking Platform

### Business context

A banking client requires low latency, strong security, and strict compliance.

### Architecture choices

- private network segmentation
- SQL with private endpoints and encryption
- centralized monitoring and audit logging
- active-passive or hot standby DR design
- strict identity and conditional access controls

### Key concern

Compliance, data protection, and resilience.

---

## Case Study 6: Hybrid Integration Platform

### Business context

A business has critical on-prem workloads and wants to connect them securely to Azure.

### Architecture choices

- ExpressRoute or VPN
- API Management for public and partner connectivity
- Service Bus for asynchronous integration
- Key Vault and private endpoints

### Key concern

Hybrid connectivity and secure integration.

---

## Case Study 7: API-First Digital Transformation

### Business context

A company wants to expose products and services through APIs to partners and internal consumers.

### Architecture choices

- API Management
- WAF and edge protection
- backend app services and queue-based worker processing
- monitoring and governance

### Key concern

API security, rate limiting, and versioning.

---

## Case Study 8: Microservices Platform on AKS

### Business context

A digital company wants a modular platform with independent services and reusable deployment patterns.

### Architecture choices

- AKS for container orchestration
- Service Bus and Kafka depending on event types
- SQL/Redis/Cosmos depending on service characteristics
- GitOps and IaC
- Centralized observability and security controls

### Key concern

Complexity management, team maturity, and supportability.

---

## 12.1 Final Case Study Template

For each design, always present:

- business context
- discovery questions
- FR and NFR
- technical requirements
- options
- selected architecture
- Azure services
- security and networking
- HA/DR and backup
- operations and monitoring
- cost and trade-offs

## 12.2 Common Interview Pattern

Client question:

“We need a secure and scalable platform with low latency and quick recovery.”

Architect answer pattern:

Business context first, then break down criticality, traffic, user geography, and compliance. Then define measurable targets, evaluate options, and explain why the selected design meets the business requirement with the right trade-offs.

---

Next step: interview preparation and answer framing.
