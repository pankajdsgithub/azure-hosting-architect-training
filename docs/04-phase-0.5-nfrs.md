# 04. Phase 0.5: Functional and Non-Functional Requirements

## 1. Concept

Simple Hinglish:

Functional requirement yeh bataata hai ki system ko kya karna chahiye. Non-functional requirement yeh bataata hai ki system kaise perform karna chahiye — kitna reliable, secure, fast, scalable, measurable hona chahiye.

Example:

- Functional requirement: user login kar sakta hai.
- Non-functional requirement: login response 2 seconds ke andar aana chahiye, aur 99.9% availability honi chahiye.

Professional interview answer:

Functional requirements define what the system must do, whereas non-functional requirements define how the system must behave in terms of performance, availability, reliability, security, maintainability, cost, and operability. NFRs are crucial because they usually drive the architecture decisions more than the functional flow itself.

## 2. Why Does a Business Need This?

Business often says, “This should be fast and always available.” But fast and always available mean different things to different people. Architect ko in requirements ko quantify karna padta hai.

Without quantification, design decisions remain subjective.

## 3. Functional Requirements (FR)

Examples:

- Customers can create and view orders.
- Admins can manage users and roles.
- APIs must allow product lookup and update.
- System must send notifications to users.
- System must support role-based access.

FR pattern:

- actor
- action
- outcome

Example:

> As a customer, I must be able to view my order status so I can track delivery.

## 4. Non-Functional Requirements (NFR)

### Key NFR categories

1. Availability
2. Performance
3. Scalability
4. Reliability
5. Resilience
6. Security
7. Compliance
8. Data protection
9. Disaster recovery
10. Maintainability
11. Observability
12. Interoperability
13. Portability
14. Cost optimization
15. Operational support

## 5. Detailed NFR Discovery Questions and Conversions

### 5.1 Availability

Business question:

- How much downtime can the business tolerate?

Why ask:

Because downtime cost may be low for internal tools but extremely high for payment or public customer apps.

Example client answer:

- “We can tolerate 4 hours of downtime per year.”

Technical interpretation:

- target availability about 99.95% or better depending on scope
- need HA design, health checks, monitoring, failover, and maintenance strategy

Quantification:

- availability target = % uptime per year
- 99.9% ≈ 43.8 minutes downtime per month
- 99.95% ≈ 21.9 minutes downtime per month
- 99.99% ≈ 4.38 minutes downtime per month

Possible architecture patterns:

- active-passive or active-active deployment
- load balancing
- autoscaling
- multi-region design for critical workloads

Azure services:

- Azure Front Door, Application Gateway, AKS, Container Apps, App Service, Availability Zones, Azure Load Balancer

Trade-offs:

- higher availability increases cost and operational complexity

### 5.2 Performance

Business question:

- What response time is acceptable to users?

Why ask:

Because performance drives network and compute sizing as well as caching and database design.

Example response:

- “The homepage must load under 3 seconds, APIs under 500 ms for normal traffic.”

Measurement:

- p95, p99 latency
- throughput (requests per second)
- concurrent users

Patterns:

- caching
- CDN
- app scaling
- query optimization
- async processing

Azure services:

- Front Door, CDN, Azure Cache for Redis, App Service, AKS, SQL performance tuning

### 5.3 Scalability

Business question:

- How much traffic growth do you expect?

Example response:

- “Traffic spikes 5x during festival season.”

Technical interpretation:

- need scaling and burst handling
- maybe queue + workers pattern

Azure services:

- VMSS, AKS autoscaling, Container Apps scale rules, Service Bus, Event Hubs, Front Door

### 5.4 Reliability

Business question:

- How often can the system fail before it is considered unacceptable?

Why ask:

This determines error-handling, retries, idempotency, and monitoring design.

Measurement:

- error rates
- failure recovery time
- mean time between failures

### 5.5 Resilience

Business question:

- What happens when a dependency fails?

Example response:

- “Order processing should continue even if downstream notification service is temporarily unavailable.”

Technical interpretation:

- asynchronous decoupling
- retry and DLQ patterns
- circuit breakers
- queue-based processing

### 5.6 Security

Business question:

- What security controls are mandatory?

Examples:

- data must be encrypted in transit and at rest
- MFA required for admin access
- no public access to databases

Technical interpretation:

- private endpoints
- RBAC
- managed identity
- Key Vault
- WAF
- conditional access

### 5.7 Compliance

Business question:

- Are there regulatory or legal requirements?

Examples:

- data residency in India
- retention for 7 years
- audit logs required

Technical interpretation:

- region selection
- policy enforcement
- encryption and logging
- retention

### 5.8 Data protection

Business question:

- How much data can be lost?
- How quickly must data be recovered?

Measures:

- RPO: recovery point objective
- RTO: recovery time objective

Example:

- RPO 15 min, RTO 1 hour

Architecture implications:

- backup schedule, replication, restore testing

### 5.9 Disaster recovery

Business question:

- What happens in the event of a regional outage?

Example response:

- “Production must failover to secondary region within 1 hour.”

Architecture patterns:

- warm standby
- active-passive
- active-active
- geo-redundancy

### 5.10 Maintainability

Business question:

- How easy should it be to deploy updates and support changes?

Technical interpretation:

- automation
- IaC
- modular deployment patterns
- environment promotion

### 5.11 Observability

Business question:

- How will the team know if the system is healthy?

Measures:

- latency, error rate, CPU, memory, application logs, traces, dashboards, alerts

Azure services:

- Azure Monitor, Log Analytics, App Insights, Workbooks

### 5.12 Interoperability

Business question:

- Which external systems must integrate with us?

Interpretation:

- API gateway
- integration services
- message-based decoupling
- file transfer or event exchange

### 5.13 Portability

Business question:

- Do we need the ability to move workloads across environments or clouds?

Interpretation:

- avoid hard dependency on one cloud-specific pattern
- standardize on containers, APIs, and open patterns

### 5.14 Cost optimization

Business question:

- What is the expected budget envelope?

Interpretation:

- choose right-size services
- prefer platform managed services when appropriate
- use autoscaling and reserved capacity strategically

### 5.15 Operational support

Business question:

- Is this a 24x7 service with L1/L2/L3 support requirements?

Interpretation:

- SRE or operations model
- alert routing
- runbooks
- SLA monitoring

## 6. SLA, SLO, SLI

### SLI

Service Level Indicator: actual measurement

Examples:

- request success rate
- API latency
- queue lag

### SLO

Service Level Objective: target value

Example:

- 99.9% API successful response rate
- p95 latency under 500 ms

### SLA

Service Level Agreement: contractual promise to customer or business

Example:

- 99.95% platform availability under defined support window

## 7. RTO, RPO, MTTR, MTBF, MTTA

### RTO

Recovery Time Objective: time to recover after failure

### RPO

Recovery Point Objective: data loss allowed

### MTTR

Mean Time To Recover

### MTBF

Mean Time Between Failures

### MTTA

Mean Time To Acknowledge

## 8. Example Quantified NFR Table

| NFR | Business question | Example answer | Technical target |
|---|---|---|---|
| Availability | How long can the app be down? | 4 hours/year max | 99.95% |
| Performance | What should APIs feel like? | p95 under 500 ms | 500 ms at normal load |
| Scalability | What happens during spikes? | 5x seasonal growth | autoscaling + queue decoupling |
| Data protection | How much data can we lose? | 15 minutes | RPO 15 mins |
| DR | How fast must recovery happen? | 1 hour | RTO 1 hour |
| Security | What security is required? | MFA and private connectivity | Entra ID + private endpoints |

## 9. Sample Business Requirement to HLD and LLD Decision Table

This section helps convert vague business phrasing into practical architecture choices that appear in both HLD and LLD.

### 9.1 HLD and LLD scenario examples

| Scenario | Business requirement | HLD design choice | LLD design choice | Architecture rationale |
|---|---|---|---|---|
| Retail e-commerce | Customer should place orders even during festive spikes, without slow checkout | Use API-driven architecture with Front Door, WAF, app tier, and message-based order processing | Deploy stateless app services, autoscaling, Redis caching, queue-based order workers, database read replicas | Prevent checkout failures under traffic bursts and decouple slow downstream steps |
| Banking / payments | Transaction must be secure, auditable, and highly available | Prefer private network segmentation, strong identity controls, and dual-region failover | Use private endpoints, managed identity, Key Vault, WAF, RBAC, encrypted storage, transaction logs, and active-passive DR | Security and compliance are higher priority than raw feature speed |
| Internal HR portal | HR dashboard must be available during working hours but does not need 24x7 demand | Use a single region with autoscaling and scheduled maintenance window | Provide app services, SQL DB, standard backups, alerts, and role-based access | Keep the design simple and cost effective while meeting business hours SLA |
| Logistics tracking | Real-time shipment updates are expected, but minor delay is tolerable | Use event-driven integration with API ingestion and asynchronous processing | Event Hubs or Service Bus for telemetry, stream processing, notifications, and DLQ | Real-time visibility is important, but the system does not need synchronous blocking at every step |
| Healthcare / patient portal | Data privacy and access control are paramount | Use zero-trust, private access, regional hosting, and strict segregation of workloads | Enforce MFA, conditional access, encryption keys in Key Vault, audit logging, and limited public access | Risk exposure from data leakage is more critical than user convenience |
| Public government portal | System must support peak traffic during new service launches | Use CDN + Front Door + load-balanced app services + autoscaling | Cache static pages, use asynchronous jobs for heavy operations, deploy with blue-green releases | Public-facing services need scale and resilience during spikes without downtime |
| Ticketing platform | Users expect quick search and order updates but not full real-time consistency | Use read-optimized front end with CQRS-style patterns where needed | Cache high-frequency queries, use separate write and read models, asynchronous notifications | Improves speed while preserving acceptable eventual consistency |
| IoT / telemetry analytics | Millions of sensor messages must be processed with minimal loss | Use event ingestion, partitioning, and streaming architecture | Event Hubs for ingestion, stream analytics or Kafka consumers, long-term storage, and alerting | Handles high throughput and allows replay or backfill |

### 9.2 Decision matrix for HLD-level requirements

| Business statement | Typical interpretation | HLD architectural answer | Typical Azure services |
|---|---|---|---|
| “We need it to be fast” | Need latency target and concurrency model | Use CDN, caching, scale-out, and performance benchmarking | Front Door, Azure CDN, Redis, AKS, App Service |
| “It must always be available” | Need uptime target and failure domain protection | Use active-active or active-passive deployment, load balancing, and DR design | Azure Front Door, Traffic Manager, Availability Zones, Load Balancer |
| “It should be secure by default” | Need identity, segmentation, and encryption | Use zero-trust model with private networking and managed identity | Entra ID, Key Vault, NSGs, WAF, Private Link |
| “We need to handle growth” | Need elasticity and burst support | Use autoscaling and asynchronous processing | AKS autoscaler, Container Apps, Service Bus, Event Hubs |
| “We need to reduce cost” | Need right-sizing and platform-managed services | Prefer PaaS over IaaS where possible; use autoscaling and standard SKUs | App Service, Azure SQL, Container Apps, Azure Monitor |
| “We need compliance” | Need region, retention, and audit controls | Design for residency, secure logging, and policy enforcement | Azure Policy, Defender, Log Analytics, Key Vault |

### 9.3 Decision matrix for LLD-level requirements

| Requirement detail | LLD design question | Typical implementation | Why it matters |
|---|---|---|---|
| API latency under 500 ms | How is caching and query optimization implemented? | Redis cache, pagination, DB indexing, async jobs | Keeps user-facing responses within SLA |
| 99.95% availability | What health checks and failover controls exist? | Liveness probes, readiness probes, deployment strategies, regional failover plan | Provides resilience during app or platform faults |
| No public DB access | How do components communicate securely? | Private endpoints, VNet integration, firewall rules, managed identity | Reduces attack surface and meets security best practice |
| High traffic during peak window | What auto-scaling rules are configured? | Horizontal pod scaling, CPU/memory thresholds, queue-based workers | Keeps service stable without oversizing always-on resources |
| Message durability required | What retry and DLQ logic is implemented? | Service Bus topics, dead-letter queues, idempotent consumers | Prevents data loss and supports recovery from transient failures |
| Business users require audit trails | What logging and trace model is implemented? | Azure Monitor, App Insights, diagnostic settings, centralized log retention | Supports governance, security review, and troubleshooting |
| Disaster recovery within 1 hour | How is backup and restore tested? | Geo-replication, backup schedule, restore runbook, failover drills | Ensures the business can recover within stated RTO |

### 9.4 Sample HLD-to-LLD traceability table

| Business objective | HLD statement | LLD implementation detail | Evidence of traceability |
|---|---|---|---|
| Provide secure customer access | Use identity-first access and WAF at edge | Entra ID + App Gateway + WAF + RBAC | Security requirements trace to access control design |
| Support seasonal traffic spikes | Scale horizontally and decouple order processing | AKS autoscaling + Service Bus queue + worker pods | Scalability requirement mapped to queue-based worker pattern |
| Meet customer SLAs | Keep app responsive and available | Redis cache, DB indexing, health probes, active-passive failover | Performance and availability targets map to runtime implementation |
| Preserve data integrity | Use transactional database and backup strategy | Azure SQL with failover group, backup retention, restore tested | Data protection requirement maps to database DR design |
| Support cross-system integration | Use event-driven communication | Service Bus topics, API gateway, integration layer | Interoperability requirement mapped to integration design |

### 9.5 Practical architect interview framing

When an interviewer asks, “What design choice would you make for this requirement?”, the correct answer should be structured like this:

1. Business need
2. Requirement quantification
3. HLD decision
4. LLD design detail
5. Trade-off and risk

Example:

> The business requires 99.95% availability for a customer-facing portal during peak shopping periods. At HLD level, we would choose a regional active-passive architecture with a global entry point, autoscaling, and traffic management. At LLD level, we would implement Azure Front Door, WAF, application load balancing, autoscaled container services, database failover, and health-based routing. The trade-off is higher cost and operational complexity, but it is justified by the business impact of downtime and the required SLA.

## 10. Common Mistakes

- NFRs written without measurable thresholds
- saying “high availability” without specifying uptime target
- not linking NFR to business impact
- selecting services before defining performance and resilience target

## 11. Interview Questions

### Basic

- What is the difference between FR and NFR?
- Why do NFRs drive architecture decisions?
- What is an SLA?

### Intermediate

- How do you convert business availability expectations into Azure design decisions?
- Why are RTO and RPO important?
- What metrics help define observability requirements?

### Advanced

- How do you handle an application with conflicting NFRs, such as low latency and strong consistency?
- How do you quantify cost against availability in architecture reviews?
- How do you decide which NFR is non-negotiable versus negotiable?

## 12. Quick Revision

- FR = what system does.
- NFR = how system performs.
- Good NFRs are measurable and tied to business risk.
- SLA, SLO, RTO, RPO are not theoretical—they drive architecture.

## 13. Knowledge Checkpoint

- What are three common NFR mistakes in solution design?
- Which NFRs usually drive database choice?
- Which NFRs usually drive network design?
- Why is a vague claim like “must be secure” not sufficient?
- What is the difference between SLO and SLA?

---

Next step: requirement-to-technical requirements conversion phase.
