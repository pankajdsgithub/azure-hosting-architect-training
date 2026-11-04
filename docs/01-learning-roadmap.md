# 01. Learning Roadmap

## 1. Concept

Simple Hinglish:

Architecture training ka asli objective yeh nahi hai ki sirf Azure services yaani App Service, AKS, SQL, Service Bus, Front Door ya Key Vault ke names yaad rakh lo. Asli kaam yeh hai ki business ko samjho, missing requirements ko identify karo, unhe measurable technical requirements mein convert karo, options evaluate karo, aur phir best-fit Azure design choose karo.

Professional interview answer:

The real purpose of an enterprise architecture study journey is to build the ability to translate business context into technical requirements, evaluate alternatives against security, cost, resilience, and operational constraints, and defend the selected solution with clear architecture rationale.

## 2. Why Does a Business Need This?

Ek enterprise client aksar kehta hai: “We need Azure.” Par actual problem yeh hota hai:

- productivity improve karni hai
- customer experience better karni hai
- compliance meet karna hai
- performance improve karna hai
- global access chahiye
- disaster recovery chahiye
- cost control maintain karna hai
- IT operations simplify karni hai

Architect ka role hai ki vo business language ko technical architecture language mein convert kare.

## 3. Learning Flow

```text
Business understanding
   -> Requirement discovery
   -> FR / NFR definition
   -> Technical requirement conversion
   -> Architecture options evaluation
   -> Azure service selection
   -> HLD + LLD
   -> Security + networking + HA/DR
   -> DevOps + monitoring + operations
   -> Cost + risk + documentation
   -> Interview-ready presentation
```

## 4. Overall Course Structure

### Phase 0: Understanding the Business and Application

- business objectives
- stakeholders
- business criticality
- current-state assessment
- application discovery
- user personas and geography
- pain points and constraints

### Phase 0.5: Functional and Non-Functional Requirements

- FR vs NFR
- availability, performance, security, backup, resiliency, compliance
- SLA, SLO, SLI, RTO, RPO, MTTR, MTBF, MTTA

### Phase 1: Requirement-to-Technical Conversion

- business requirement to technical requirement
- requirement traceability
- measurable design decisions
- architecture options and trade-offs

### Phase 2: Database Architecture

- relational vs non-relational
- transactional consistency and latency needs
- SQL, Cosmos DB, Redis, storage strategies
- microservices data patterns

### Phase 3: Messaging and Event-Driven Architecture

- Service Bus
- Kafka
- Event Hubs
- Event Grid
- queue vs stream vs event mesh
- replay, idempotency, retries, DLQ

### Phase 4: Compute, Networking, Landing Zone

- app hosting decisions
- VNet, NSG, Firewall, Front Door, Application Gateway, private endpoints
- Azure landing zone and governance

### Phase 5: Security and Governance

- IAM, RBAC, Key Vault, private endpoints, Defender, policy, zero trust

### Phase 6: HA/DR/Operations

- availability zones, region pairs, backup, restore, support model, on-call, incident management

### Phase 7: DevOps, Observability, and IaC

- Azure DevOps/GitHub
- Terraform/Bicep
- pipelines, drift, approvals, GitOps
- Azure Monitor, App Insights, logs, alerts

### Phase 8: Case Studies and Interview Practice

- enterprise case studies
- structured answer frameworks
- client-facing communication

## 5. Architect Mindset

A senior architect does not ask:

- “Which Azure service should we use?”

He asks:

- “What business outcome do we need?”
- “What is the real risk if this fails?”
- “What are the user expectations?”
- “What constraints do we have?”
- “What is the simplest architecture that meets the requirement securely and supportably?”

## 6. Key Outcome

By the end of this study path, you should be able to explain architecture with this flow:

Business context → requirements → options → decision → risk → trade-offs → operations → documentation.

## 7. Architecture Decision Framework

```text
Client need
   -> Ask discovery questions
   -> Convert to FR/NFR
   -> Translate to technical requirement
   -> Select design options
   -> Compare alternatives
   -> Choose service architecture
   -> Validate security, HA/DR, cost, operations
   -> Document ADR / HLD / LLD
```

## 8. Quick Revision Points

- Business first, Azure second.
- NFRs must be quantifiable.
- Good architecture is not the most complex architecture.
- Every decision has trade-offs.
- Security and operations are design inputs, not post-processing.
- A good architect explains why, not just what.

## 9. Interview Question Example

Q: What is the most important thing an architect should do before choosing Azure services?

Answer: Understand the business problem, expected load, user geography, compliance, security, operational model, dependencies, and risk tolerance. Only after that should services be selected.

## 10. Knowledge Checkpoint

Answer these mentally:

- What is the difference between business requirement and technical requirement?
- What is the difference between availability and disaster recovery?
- Why is NFR quantification important?
- What is an architect trying to optimize beyond technology?
- Why do alternative designs matter in architecture interviews?

---

## 11. Next Step

Proceed to the requirement discovery framework and then to Phase 0 business discovery.
