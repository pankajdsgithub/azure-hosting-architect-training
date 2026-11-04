# 03. Phase 0: Business and Application Understanding

## 1. Concept

Simple Hinglish:

Architecture ka real start business understanding se hota hai. Agar client ki business ko samjha nahi gaya, toh aap design karte time galti kar sakte ho. Business understanding ka matlab hota hai: product kya hai, customer kaun hai, application kis purpose se use hota hai, kin business processes par dependency hai, aur kis level ki availability aur performance required hai.

Professional interview answer:

Phase 0 focuses on understanding the business context, application portfolio, operating model, stakeholders, user expectations, business criticality, and risk profile before any Azure service selection. This ensures architecture decisions are driven by business needs rather than platform preference.

## 2. Why Does a Business Need This?

Ek architecture team ko yeh samajhna chahiye:

- application kis business capability ko enable karta hai
- workloads kitne critical hain
- downtime kitna expensive hai
- users kis geography se access karte hain
- app kitni traffic handle karni padegi
- data and compliance constraints kya hain

Without this understanding, the architect may overdesign or underdesign the platform.

## 3. Business Understanding Topics

### A. Business objectives

Questions:

- Business objective kya hai?
- Kya company grow, optimize, or modernize karna chahti hai?
- Kya project revenue growth, automation, better customer experience, or compliance enablement ke liye hai?

Why ask:

Because architecture should align to business value, not just technical modernization.

Example answers:

- “We want to improve customer self-service and reduce manual support effort.”
- “We need digital transformation for faster order processing and better visibility.”

Technical interpretation:

- need digital experience layer
- API integration
- support workflows and monitoring

Follow-up question:

- What business KPIs define success?

### B. Business capabilities

Questions:

- Which core business capabilities are enabled by this solution?
- Kya solution revenue generation, support, operations, or compliance enablement ke liye hai?

Why ask:

This helps prioritize workloads and critical path functions.

### C. Business-critical applications

Questions:

- Kya app directly revenue or customer trust se related hai?
- Which applications are critical to operations?

Why ask:

Critical applications require stricter availability, security, and operational standards.

### D. Business processes

Questions:

- Kaunse business process automate honge?
- Which process is the main flow?
- Are there batch steps, manual approvals, or exception handling?

Why ask:

Business process shape determines whether asynchronous processing, event-driven workflows, or transactional design is needed.

### E. Revenue-critical workloads

Questions:

- Which workloads directly generate revenue?
- Are there peak windows like end-of-month, festival, launch, or quarter-end?

Why ask:

These workloads drive capacity planning, autoscale design, and cost controls.

### F. Internal vs customer-facing

Questions:

- Kya application internal employee use ke liye hai ya customer-facing?
- Is it partner or external API exposure?

Why ask:

Public-facing applications have more stringent security, WAF, DDoS, and latency requirements.

### G. Application ownership

Questions:

- Application owner kaun hai?
- Product owner and support owner kaun hain?

Why ask:

Ownership impacts decision-making, change approval, and support responsibilities.

### H. Stakeholders and personas

Questions:

- Kaun users hain?
- Are they internal users, public customers, support teams, admins, or external partners?

Why ask:

Different personas require different access patterns, UX, and security controls.

### I. User geography

Questions:

- User majority kis geography se hai?
- Kya global access chahiye?

Why ask:

This drives regional placement, edge routing, latency expectations, and DR strategy.

### J. Business operating hours

Questions:

- Application 9-to-5 ka hai ya 24x7?
- Is support window defined?

Why ask:

Operating hours affect support model, maintenance window, SLA, and capacity planning.

### K. Business growth expectations

Questions:

- Business next 1-3 years mein kitna grow karna chahta hai?
- Are there seasonal spikes or new regions?

Why ask:

Growth assumptions must be reflected in autoscale and regional design.

### L. Business continuity expectations

Questions:

- Business continuity kitni important hai?
- Kya application downtime serious revenue loss create karta hai?

Why ask:

Business continuity directly drives HA and DR architecture.

### M. Business constraints

Questions:

- Kya budget constraints hain?
- Kya procurement cycles or compliance restrictions hain?
- Kya legacy system dependency hai?

Why ask:

Constraints bind the architecture and influence trade-offs.

### N. Existing pain points

Questions:

- Current system mein kya issue hai?
- Slow performance, frequent outage, lack of visibility, manual operations, poor scalability?

Why ask:

The pain points define modernization scope and architecture priorities.

## 4. Application Discovery

### A. New vs existing app

- New application: freedom to design cloud-native from scratch
- Existing application: integration and modernization complexity

### B. Monolith vs microservices

- monolith: simpler to start; may need decomposition later
- microservices: modularity and scale; more operational complexity

### C. Three-tier architecture

Common pattern:

- presentation tier
- application tier
- data tier

This influences load balancing, API design, security zones, and scaling.

### D. Web applications

- static or dynamic
- internal portal or public internet app
- authentication and routing patterns matter

### E. APIs

- public APIs
- partner APIs
- internal service APIs
- rate limiting and governance required

### F. Batch processing

- monthly reconciliation
- ETL
- message processing
- large compute workload patterns

### G. Background workers

- async jobs
- notifications
- data transformations
- long-running workflows

### H. Event-driven applications

- order placement events
- streaming analytics
- asynchronous decoupling

### I. Stateful vs stateless

- stateless: easier to autoscale
- stateful: needs persistence, sticky sessions, or data service strategy

### J. Legacy applications

- old OS or difficult licensing
- usually require modernization, lift-and-shift, or refactoring strategy

### K. Containerized workloads

- Docker/Kubernetes portability
- more automation and orchestration required

### L. Server-based workloads

- need VM or VMSS
- OS control and legacy dependency may drive this choice

## 5. Current-State Assessment

Architect should discover:

- existing infrastructure: on-prem VMware, bare metal, server counts
- current Azure subscriptions and landing zone status
- network segmentation and connectivity
- existing databases and schema complexity
- middleware stack and integrations
- monitoring and logging setup
- backup and DR arrangements
- deployment pipeline maturity
- support operations model

### As-Is architecture

This includes current components and how they interact.

### Gap analysis

- what is missing in security, monitoring, network, automation, or DR?
- what is blocking cloud-readiness?

### To-Be architecture

This is the target design based on future state and standards.

## 6. Example Business-to-Architecture Interpretation

Client says:

“We have a customer portal and order processing system that is slow during festival sales. We also need to integrate with SAP and must ensure zero data loss for order data.”

Architect interpretation:

- public-facing web and API workload
- high seasonal demand and bursty load
- database and messaging design must support strong consistency and durability
- SAP integration likely through API, events, or file-based integrations
- strict backup and RPO considerations
- need autoscaling, load balancing, monitoring, and operational readiness

## 7. Common Mistakes

- jumping directly to Azure services without understanding business
- assuming all apps are cloud-native
- ignoring legacy constraints
- not discovering support model and operating responsibilities
- ignoring growth and seasonal demand

## 8. Interview Questions

### Basic

- What is business context discovery in architecture?
- Why is application discovery important before selecting Azure services?
- What is as-is and to-be architecture?

### Intermediate

- How do you determine whether an application is a good fit for Azure-native modernization?
- What questions help identify whether a workload is stateless or stateful?
- What gap analysis points usually emerge in legacy modernization programs?

### Advanced

- How do you handle a client with no clear business requirement but a push to move to Azure?
- How do you identify the real criticality of an application without being misled by stakeholder language?
- What evidence is required before recommending a redesign or modernization plan?

## 9. Quick Revision

- Business and application understanding is the foundation of architecture.
- Architecture is not just technical design; it is business translation.
- Current-state assessment reveals gaps that must be solved.
- A good architecture is rooted in business criticality, user impact, and constraints.

## 10. Knowledge Checkpoint

- What identified information helps you determine if the app is public-facing or internal?
- How do you assess whether an application is a good candidate for microservices?
- What is the difference between current-state assessment and target-state architecture?
- Why do business growth assumptions affect capacity design?
- What is the value of gap analysis before architecture design?

---

Next step: Phase 0.5 – Functional and Non-Functional Requirements.
