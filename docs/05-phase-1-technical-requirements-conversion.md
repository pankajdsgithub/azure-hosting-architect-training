# 05. Phase 1: Requirement-to-Technical Architecture Conversion

## 1. Concept

Simple Hinglish:

Yeh phase sabse important hai. Business requirement ko technical requirement mein convert karna hi architecting ka asli core hai. Isme aap business ko samajh kar poochte ho, requirement ko detail mein break karte ho, aur phir validate karte ho ki konse Azure services, networking, security, HA, DR, monitoring, ops model best fit hain.

Professional interview answer:

This phase is where business intent becomes measurable technical architecture decisions. The architect moves from problem discovery to requirement definition, option analysis, platform selection, and design validation using constraints such as performance, security, cost, and operational supportability.

## 2. Why Does a Business Need This?

A business requirement is usually expressed in vague language:

- “We need a fast system.”
- “We need secure access.”
- “It should scale.”
- “It should be available all the time.”

Architect ko inko convert karna hota hai into:

- service behavior
- network paths
- security controls
- data placement
- scaling strategy
- monitoring model

## 3. Conversion Pattern

For every business requirement, use this exact structure:

1. Business Requirement
2. Questions Asked by Architect
3. Why Each Question Is Necessary
4. Possible Client Responses
5. Functional Requirement
6. Non-Functional Requirement
7. Technical Requirement
8. Architecture Options
9. Azure Services
10. Alternative Technologies
11. Why Select a Particular Option?
12. Security Considerations
13. Availability Considerations
14. DR Considerations
15. Performance Considerations
16. Cost Considerations
17. Operational Considerations
18. Risks and Limitations
19. Follow-up Questions
20. Final Architecture Decision
21. Sample Interview Answer

## 4. Example Scenario 1: 50,000 Concurrent Users

### 1. Business requirement

The application must support 50,000 concurrent users during peak periods.

### 2. Questions asked by architect

- What is the peak time pattern?
- Is load predictable or bursty?
- Is the workload read-heavy or write-heavy?
- Is traffic globally distributed?
- What is response time expectation?
- Are there external dependencies or upstream bottlenecks?

### 3. Why necessary

To estimate scale needs, routing design, and whether caching, Async processing, or regional distribution is required.

### 4. Possible client responses

- “Traffic spikes during festival season.”
- “80% read traffic, 20% write traffic.”
- “Users are in India and the Middle East.”

### 5. Functional requirement

The system must provide a scalable public-facing user experience for peak demand.

### 6. NFR

- p95 latency under 2 seconds
- 99.9% availability
- autoscaling support

### 7. Technical requirement

- app services must be stateless and horizontally scalable
- ingress and routing must support high traffic
- database and caching strategy must handle read traffic efficiently

### 8. Architecture options

- Azure App Service / Container Apps / AKS
- Front Door or Application Gateway for ingress
- Azure Cache for Redis
- SQL read replicas or CDN for static assets

### 9. Azure services

- Azure Front Door
- Azure CDN
- App Service or AKS
- Azure Cache for Redis
- Azure SQL Database
- Azure Monitor

### 10. Alternative technologies

- VMSS with custom load balancer
- dedicated VMs with no platform autoscaling
- using static apps with separate API layer

### 11. Why select a particular option?

If the app is containerized and needs elasticity and DevOps agility, AKS or Container Apps may be the right choice. If it is simpler and not container-heavy, App Service may reduce complexity.

### 12. Security considerations

- WAF policy
- private backends
- managed identity
- secrets in Key Vault

### 13. Availability considerations

- multi-AZ or multi-region if required
- health probes
- backend redundancy

### 14. DR considerations

- region failover strategy if business critical

### 15. Performance considerations

- CDN for static content
- caching for hot reads
- load test and capacity planning

### 16. Cost considerations

- Autoscale can increase cost only at peak demand
- Overprovisioning is wasteful
- Need right-sizing based on measured burn and SLA

### 17. Operational considerations

- monitoring dashboards needed
- support team readiness
- release windows must be defined

### 18. Risks and limitations

- cache invalidation complexity
- database bottlenecks if write-heavy
- hidden regional dependencies

### 19. Follow-up questions

- Is the workload bursty or continuous?
- Do we need regional failover?
- Are there single points of failure already in the app layer?

### 20. Final architecture decision

Use a public edge layer with autoscaling app services, Redis for caching, and SQL database sized for expected peak and growth, with monitoring and a regional failover plan if required.

### 21. Sample interview answer

We would first quantify the workload, understand peak pattern, and validate whether the UI and API are stateless and horizontally scalable. Based on that, we would design a public ingress layer with WAF and auto-scaling app services, a caching layer for hot read traffic, and a database strategy sized for concurrency while avoiding a single write bottleneck. We would also validate security, observability, and potential regional failover if the workload is business critical.

---

## 5. Example Scenario 2: Application Must Recover Within One Hour

### Business requirement

The system must recover within one hour after a regional failure.

### Conversion flow

- RTO = 1 hour
- need DR plan
- likely warm standby, active-passive, region-pair architecture
- data replication and restore process required

### Architecture options

- active-passive dual region
- active-active with load distribution
- pilot-light for low-cost DR

### Azure services

- Azure Traffic Manager or Front Door
- Azure SQL failover groups
- Storage account GRS/RA-GRS
- Azure Site Recovery for VM workloads
- Azure Monitor and alerts

### Decision logic

If the application is not fully business-critical but needs quick recovery, warm standby may be sufficient. If customer experience is critical, active-active may be required.

## 6. Example Scenario 3: Data Loss Must Not Exceed 15 Minutes

### Business requirement

The application must not lose more than 15 minutes of production data in a failure event.

### Interpretation

- RPO = 15 min
- need continuous or near real-time replication
- database and storage must support point-in-time restore or replication controls

### Azure services

- Azure SQL failover groups
- Azure storage replication
- database backup and retention policies
- Azure Backup
- region-pair strategy

## 7. 30 Business Scenarios to Practice

1. 50,000 concurrent users
2. 99.95% portal availability
3. 1-hour recovery target
4. 15-minute data loss tolerance
5. Global customer access
6. Unpredictable traffic spikes
7. Legacy SAP integration
8. Asynchronous order processing
9. Event replay and recovery
10. Real-time analytics pipeline
11. Relational transaction-heavy database
12. Global customer profile data
13. Multi-tenant platform for multiple clients
14. Minimal downtime release process
15. Private connectivity from on-premises apps
16. Data residency constraint in specific geography
17. 24x7 support model
18. Cost-sensitive platform for non-critical workloads
19. High-volume telemetry ingestion
20. Transactional e-commerce application
21. Notification system with retry and DLQ
22. Batch reporting workload
23. Customer access through public internet with strong WAF requirements
24. Internal employee support portal
25. Inventory system with eventual consistency and asynchronous sync
26. Payment processing with strong audit traceability
27. API-first integration platform
28. Financial reporting requiring analytics and retention
29. Disaster recovery for business-critical application
30. Modernization of on-prem monolith to Azure

## 8. Final Architect Guidance

Do not try to design from service names alone. Design from:

- business criticality
- user behavior
- data and consistency needs
- security and trust
- failure modes
- cost and operations

## 9. Common Mistakes

- treating NFR as a nice-to-have
- assuming all workloads require AKS
- mapping single requirement to single Azure service without evaluating alternatives
- ignoring operational support model
- not asking follow-up questions to clarify ambiguity

## 10. Interview Questions

### Basic

- How do you convert a business requirement into a technical requirement?
- Why is requirement conversion important in Azure architecture?
- What is the difference between a business requirement and a functional requirement?

### Intermediate

- Give an example of a requirement that changes the entire architecture.
- How do you handle requirements that are not well defined?
- How do you prioritize competing NFRs?

### Advanced

- How would you respond if the client asks for 99.99% uptime but has no budget for multi-region deployment?
- What is the difference between architectural choice and technical preference?
- How do you document trade-offs in an architecture decision record?

## 11. Quick Revision

- Translate business statements into technical, measurable requirements.
- Quantify all NFRs.
- Architecture decisions should be justified by business need, not by trend.
- Every requirement should trigger an evaluation of options, risks, and costs.

## 12. Knowledge Checkpoint

- Which questions must be asked before choosing a database?
- Which questions must be asked before choosing messaging technology?
- Why do RTO and RPO change the architecture significantly?
- What is the value of a decision matrix in architecture reviews?
- Why is a trade-off analysis required in every enterprise design?

---

Next step: database architecture and technology selection.
