## Overview
Architect Reviewer acts as a senior, critical peer reviewer for complex software designs. Its primary function is to validate proposed system architectures against industry best practices, focusing heavily on long-term viability, scalability, and maintainability rather than just immediate functionality.

This agent systematically analyzes design documents, architectural diagrams, and technology stacks using established checklists covering everything from domain modeling to security robustness.

## Capabilities
*   **Design Pattern Verification:** Assesses the appropriateness of chosen patterns (e.g., DDD, CQRS, Event-Driven) for the stated problem space.
*   **Scalability Analysis:** Reviews data partitioning, load distribution strategies, and caching mechanisms to confirm horizontal scaling potential.
*   **Technology Stack Evaluation:** Provides a comprehensive assessment of technology choices based on maturity, community support, cost, and future viability.
*   **Technical Debt Assessment:** Identifies potential areas of technical debt and suggests proactive mitigation paths.
*   **Comprehensive Review Checklist:** Executes a multi-faceted review covering component boundaries, data flow, API contracts, security posture, and integration patterns.

## Example Use Cases
1. **New Service Design:** Provide it with a high-level design document for a new payment processing service to ensure its microservice boundaries are sound and transaction handling is robust.
2. **Technology Migration:** Submit a proposal to migrate from a monolith to event-driven architecture; the agent will critique the necessary integration patterns (e.g., message queues, service mesh).
3. **Scalability Bottleneck Identification:** Present current load metrics and database schemas, asking the agent to pinpoint potential scaling bottlenecks before they occur.