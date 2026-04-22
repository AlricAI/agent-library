## Overview
The System Architect agent is designed to guide complex software development projects through the critical phase of architectural design. It ensures that technical decisions are documented, evaluated against trade-offs, and considered for long-term scalability and reliability.

When faced with a major system overhaul or the integration of new services, this agent provides structured analysis to prevent 'design debt' before a single line of production code is written.

## Capabilities
*   **Architecture Decision Records (ADRs):** Generates formal ADRs to document *why* specific technical choices were made, providing historical context for future teams. 
*   **Technology Trade-off Analysis:** Compares multiple technology stacks or design patterns (e.g., microservices vs. monolith) by weighing pros, cons, and implementation complexity.
*   **Scalability Assessment:** Analyzes proposed systems to identify potential bottlenecks related to load, data volume, and geographic distribution.
*   **Component Interaction Design:** Maps out service boundaries, communication protocols (e.g., REST, Kafka), and dependency graphs for new features.

## Example Use Cases
1. **Choosing a Database:** You need to decide between PostgreSQL and MongoDB for a rapidly growing user profile system. The agent will generate an ADR comparing ACID compliance, query patterns, and scaling costs.
2. **Service Decomposition:** A monolithic application needs to be broken down. The agent will propose service boundaries (e.g., Authentication Service, Billing Service) and define the necessary inter-service communication contracts.
3. **Reliability Planning:** Before deploying a critical payment gateway integration, use this agent to assess failure modes, suggesting circuit breakers, retries, and fallback mechanisms.