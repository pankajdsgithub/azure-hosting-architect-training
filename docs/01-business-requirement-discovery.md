# 01. Business Requirement Discovery

The first task in any architecture engagement is to understand the business problem and the real operating model. A good architect does not start from technology; they start from why the solution exists.

## Goals of this phase

- Understand the business objective
- Identify the key stakeholders and end users
- Discover constraints, risk, and compliance obligations
- Clarify expected scale, availability, and performance
- Determine technical success criteria from the business point of view

## Example discovery questions

### Business context

- What business problem are we solving?
- What is the expected business value of this solution?
- Who are the primary users and who are the secondary users?
- What current process or system is being replaced or improved?
- What is the expected go-live timeline?

### Scope and stakeholders

- Which teams are involved in the solution?
- What are the business owners, product owners, and operational owners?
- What are the dependencies on other teams or systems?
- Do we need internal-only, partner-facing, or public-facing access?

### Functional behavior

- What actions must the users perform?
- What does the system need to produce or expose?
- Which workflows are critical for daily operation?
- Are there integration points with external systems?

### Compliance and risk

- Are there regulatory requirements like PCI, HIPAA, GDPR, or SOC?
- Do we need data residence or residency constraints?
- What security policies are mandatory?
- What is the business tolerance for downtime or data loss?

### Performance and scale

- How many users or transactions are expected?
- Are there peaks that must be handled predictably?
- What latency is acceptable for normal and peak workloads?
- Does the application need to scale horizontally or vertically?

### Operational model

- Who will operate the solution after deployment?
- What are the expected support hours?
- Is on-call coverage required?
- What are the alert and severity expectations?

## Example business scenario

A retail company wants to launch a digital customer platform to support ordering, account management, and service interactions across web and mobile channels. The leaders want:

- a secure customer experience
- near-real-time order visibility
- support for seasonal peaks
- minimal downtime during business hours
- integration with shipping, payment, and notification systems

## Business-to-architecture translation

From this scenario, the architect begins to infer:

- need for secure public-facing entry points
- need for API management and authentication
- need for scalable application services
- requirement for monitoring and alerting
- requirement for data protection and identity controls
- need for future expansion into multiple regions or environments

## Output of this phase

The business discovery phase should produce:

- problem statement
- target users and personas
- scope and boundaries
- assumptions and constraints
- risk and compliance overview
- initial high-level success criteria

## Best practice

Document everything as a formal requirement set early. This reduces ambiguity and helps avoid designing for a solution that does not match the real need.
