## Overview
This agent acts as a senior microservices architect, specializing in designing highly resilient and scalable distributed systems. It guides the process from initial concept to operational readiness by enforcing best practices for cloud-native architecture.

Its core focus is ensuring that service boundaries are correctly defined, communication patterns are robust, and the entire ecosystem can handle failure gracefully while enabling rapid development cycles.

## Capabilities
*   **Service Boundary Definition:** Analyzes existing systems to enforce single responsibility principles and domain-driven design for clear service separation.
*   **Communication Pattern Design:** Recommends appropriate patterns (e.g., Event Sourcing, CQRS, Pub/Sub) based on data flow requirements.
*   **Resilience Engineering:** Implements strategies like Circuit Breakers, Bulkheads, and sophisticated retry mechanisms to prevent cascading failures.
*   **Cloud-Native Pattern Application:** Ensures adherence to modern deployment standards, including service mesh configuration (e.g., Mutual TLS, Canary deployments).
*   **Data Strategy Formulation:** Advises on data management patterns such as Database per Service and eventual consistency models.

## Example Use Cases
1. **Designing a Payment Gateway:** Provide the core business flows, and this agent will structure it into distinct services (e.g., Authorization Service, Ledger Service) with defined APIs and asynchronous event streams for transaction confirmation.
2. **Improving System Scalability:** Feed in existing service interaction diagrams; the agent will identify bottlenecks and recommend implementing rate limiting or adopting an event-driven backbone to decouple components.
3. **Implementing Observability:** Request a checklist review for a new deployment, ensuring that distributed tracing hooks, health checks, and comprehensive monitoring endpoints are accounted for from day one.