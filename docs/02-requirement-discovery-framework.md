# 02. Requirement Discovery Framework

## 1. Concept

Simple Hinglish:

Client ke saath meeting mein architect ka kaam shuru hota hai business ko understand karne se. Agar aapne business ko samjha nahi, toh Azure service selection random ho jayega. Requirement discovery framework ek structured method hai jisse architect clear questions pooche, missing context identify kare, aur technical design banaane ke liye right inputs collect kare.

Professional interview answer:

A requirement discovery framework is the structured process an architect uses to understand the business problem, identify constraints, confirm assumptions, and translate ambiguous business statements into measurable technical requirements before selecting platforms, services, or deployment models.

## 2. Why Does a Business Need This?

Business stakeholders often say things like:

- “We need a better application.”
- “We want Azure migration.”
- “We need higher availability.”
- “Our users are complaining about performance.”

But in reality, architect ko yeh jaana chahiye:

- kya business goal hai?
- kya problem hai?
- kaun users hain?
- kis workload ke liye solution chahiye?
- what is the priority: cost, speed, availability, security, or agility?

Without this, architecture team may overbuild or underbuild the solution.

## 3. Discovery Framework

```text
1. Understand business objective
2. Understand stakeholders and users
3. Understand current state and pain points
4. Understand application behavior and workload type
5. Capture business constraints and compliance
6. Identify critical flows and integration points
7. Define FR and NFRs
8. Quantify all measurable targets
9. Evaluate architecture options
10. Document decisions and trade-offs
```

## 4. Architect Questions by Category

### A. Business objective

- What is the business problem we are solving?
- What outcome is required?
- Which business process is critical?
- Which customers or users will depend on this solution?
- What are the business success metrics?

### B. Stakeholders and ownership

- Who owns this initiative?
- Who owns the application after go-live?
- Who is accountable for performance, security, and budget?
- Are there separate DevOps, support, security, and database teams?

### C. Application and workload

- Is it a new build or modernization of an existing app?
- Is the app monolith or microservice-based?
- Is it customer-facing or internal-facing?
- Is it batch, online transaction, event-driven, or stream processing?

### D. Current-state assessment

- What exists today on-prem or in Azure?
- Which technologies are already used?
- What are the current pain points?
- What systems must remain integrated?

### E. Availability and resilience

- What is the acceptable downtime?
- What is the RPO and RTO expectation?
- Is 24x7 support required?
- Are there regulated workloads or specific compliance controls?

### F. Performance and scaling

- How many concurrent users are expected?
- What are peak and seasonal traffic patterns?
- What response time is acceptable?
- Is the application bursty or steady state?

### G. Security and governance

- Where will data reside?
- What security controls are mandatory?
- Is private connectivity required?
- Are there identity or federation requirements?

## 5. Why Are These Questions Important?

Each question helps avoid wrong assumptions.

Example:

If a client says “We need high availability” but does not quantify it, the architect must ask:

- 99.9% or 99.95%?
- is that for application tier, database, or entire platform?
- what is business downtime tolerance?

Without quantification, “high availability” is vague.

## 6. Example Client Answers and Technical Interpretation

| Business statement | Technical interpretation |
|---|---|
| “We support 300,000 users at peak.” | Need autoscaling and possible global routing |
| “We cannot lose more than 15 minutes of data.” | RPO <= 15 min, backup/replication design needed |
| “The app must be online 24x7.” | HA, monitoring, alerting, support model required |
| “Customers are in India and the US.” | Multi-region or latency-aware design needed |
| “We must integrate with SAP and legacy systems.” | Middleware, secure connectivity, API patterns matter |
| “The app is currently monolithic.” | Need modernization assessment, not just lift-and-shift |

## 7. Requirement Conversion Pattern

```text
Business context
   -> Functional requirement
   -> Non-functional requirement
   -> Technical requirement
   -> Architecture option
   -> Azure service selection
   -> Security, DR, cost, operational review
```

## 8. Example Use Case

Client: “We need an e-commerce platform supporting Indian and global customers.”

Architect analysis:

- likely internet-facing web traffic
- API and app services needed
- database and order processing need strong consistency
- messaging may be needed for order processing and notifications
- global access may imply edge routing and regional deployment
- security and compliance matters for payment and customer identity

## 9. Follow-up Questions

- What is the customer experience expectation in latency terms?
- Is the platform transactional and critical?
- Are there payment and PII requirements?
- How many regions are expected initially?
- How do you plan to support release management and rollback?

## 10. Common Mistake

Junior engineers ask, “Which service should we use?”

Senior architects ask, “What is the problem, what is the failure mode, what are the constraints, and what is the simplest secure design?”

## 11. Architect’s Final Decision Document

The discovery output should be captured as:

- business objective
- stakeholders
- assumptions
- constraints
- risks
- FR and NFR
- current-state gaps
- target architecture approach

## 12. Interview Questions

### Basic

- What is requirement discovery in architecture?
- Why is business understanding important before Azure design?
- What is a functional requirement?
- What is a non-functional requirement?

### Intermediate

- How do you convert business objectives into technical requirements?
- What are the most important discovery questions in a migration project?
- How do you validate that a requirement is measurable?

### Advanced

- How do you handle a client who says “we need high availability” but cannot quantify the requirement?
- What strategy do you use to uncover hidden requirements in stakeholder interviews?
- How do you document assumptions and gaps when the client lacks clarity?

## 13. Quick Revision

- Requirements must be discovered, not assumed.
- Questions reveal hidden business constraints.
- Every requirement should eventually become measurable and testable.
- Good architects turn ambiguous client language into technical design input.

## 14. Knowledge Checkpoint

Answer these:

1. What is the difference between a business requirement and a technical requirement?
2. Why is a vague requirement dangerous?
3. What is the role of a discovery framework in Azure architecture?
4. Why do we need both FR and NFR?
5. What are examples of hidden requirements not explicitly stated by the client?

---

Next step: move to Phase 0 business and application discovery.
