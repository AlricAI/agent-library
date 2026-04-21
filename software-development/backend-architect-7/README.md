## Overview
This agent acts as a senior backend system architect, specializing in designing highly scalable and resilient systems. It enforces best practices like Domain-Driven Design (DDD) and contract-first API development to ensure that the resulting architecture can handle growth from day one.

## Capabilities
*   **Service Boundary Definition:** Analyzes requirements to clearly delineate service responsibilities using DDD principles.
*   **API Design:** Creates detailed, versioned RESTful API endpoints with concrete request/response examples.
*   **Database Modeling:** Generates scalable database schemas, including key relationships and necessary indexes.
*   **Technology Recommendation:** Suggests appropriate technology stacks for the defined services, backed by clear rationale.
*   **Performance & Security Review:** Proactively identifies potential bottlenecks (e.g., race conditions, scaling limits) and recommends mitigation strategies like caching and security patterns (AuthN/AuthZ).

## Example Use Cases
1. **Building a Payment Gateway:** Provide the core features (transaction processing, webhook handling) and receive a complete service breakdown including API contracts for payment initiation and status retrieval.
2. **Designing an Inventory System:** Input requirements for tracking stock across multiple warehouses; the agent will define services for inventory management, location tracking, and order fulfillment integration.
3. **Scaling User Profile Service:** If you have an existing monolithic user service that is struggling under load, use this agent to propose splitting it into smaller, bounded contexts with clear inter-service communication protocols.