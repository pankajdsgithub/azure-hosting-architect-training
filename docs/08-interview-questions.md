# 08. Interview and Review Questions

These questions are useful for architecture review, study, and interview preparation.

## Business discovery questions

- What business problem is the architecture trying to solve?
- Who are the users and what are their expectations?
- What are the expected business growth and peak periods?
- What constraints exist in time, budget, and compliance?
- Which systems will this solution integrate with?

## FR/NFR questions

- What are the key business features this platform must provide?
- Which requirements are mandatory versus optional?
- Which NFRs determine design choices?
- How do you measure scalability and performance?
- How do we define recovery and availability targets?

## Technical conversion questions

- Which Azure services align with each requirement?
- What is the ingress model?
- How is identity and authorization managed?
- Where do we place secrets, certificates, and configuration?
- What are the high-value risks if the design is implemented incorrectly?

## Landing zone questions

- What should be centralized in the landing zone?
- How do we separate dev, test, and prod?
- Which resources should be restricted by policy?
- What governance and audit controls are mandatory?

## HLD questions

- What are the major components and trust boundaries?
- What are the key integration patterns and failure domains?
- How does the design support resiliency and scale?
- How does the architecture map to the business goals?

## LLD questions

- What exact Azure services and networking settings are chosen?
- Are the services public or private?
- What monitoring and alerting are configured?
- What backup, restore, and rollback plans exist?

## Final interview-style scenario

> A business wants to launch a secure, multi-region digital customer platform with APIs, a database, event-driven processing, and enterprise-grade monitoring. Explain how you would discover requirements, convert them to technical need, and design the solution.

A strong answer should include:

- business discovery
- FR/NFR definition
- technical requirement mapping
- landing zone design
- HLD and LLD
- diagrammatic explanation
- security, operability, and risk considerations

## Study reminder

Architecture is not just about selecting products. It is about translating business reality into an implementable, secure, scalable, and governable solution.
