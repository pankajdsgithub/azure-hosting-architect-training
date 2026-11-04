# 06. Low-Level Design (LLD)

A Low-Level Design describes the concrete implementation details required to build and operate the solution.

## LLD purpose

The LLD explains:

- component-level configuration
- specific resource choices
- network settings and access paths
- workload logic and data flow
- deployment and operational controls

## Example LLD details

### Ingress and routing

- Front Door configured with WAF policy
- custom domains and TLS certificate
- specific origin groups and rules
- health probes for backend endpoints

### Application layer

- containerized services deployed in Azure Container Apps or AKS
- autoscaling based on CPU and HTTP concurrency
- ingress enabled only through private or managed routing paths
- health probes configured per service

### Data layer

- Azure SQL Database with private endpoint
- Redis for caching and transient state
- Storage account for static assets and operational files
- backup retention rules and restore testing

### Security controls

- Managed identities assigned to workloads
- Key Vault reference to secrets and certificates
- private endpoints for database and storage services
- network rules restricting access to app subnet

### Messaging and async processing

- Service Bus topics for event-driven workloads
- dead-letter queue handling
- retry and backoff policies
- consumer scaling strategies

### Monitoring and observability

- Application Insights instrumentation
- Azure Monitor alerts for latency, errors, and resource thresholds
- Log retention policy enabled
- dashboards for platform and service-level metrics

## Example LLD structure

```text
Client
  -> Front Door + WAF
      -> APIM / App Gateway
          -> API Service
              -> Azure SQL / Redis / Storage
              -> Service Bus / Event Consumers
                  -> Monitoring + Alerts + Log Analytics
```

## LLD documentation should answer

- What resource names and services are used?
- Which VNet/subnet does each service use?
- Are the resources public or private?
- Which secrets and certificates are stored where?
- What are the backup and restore procedures?
- How does deployment automation work?

## Best practice

The LLD is the basis for implementation by engineering teams and infrastructure automation. It should be precise, reviewable, and actionable.
