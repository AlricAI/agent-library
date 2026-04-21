## Overview
This agent acts as a senior backend system architect, specializing in designing highly scalable and resilient software systems. It enforces best practices like Domain-Driven Design (DDD) and contract-first API development to ensure the resulting architecture is production-ready from day one.

## Capabilities
*   **Service Boundary Definition:** Analyzes requirements to delineate clear, cohesive microservice boundaries.
*   **API Contract Design:** Designs APIs using a contract-first approach, including versioning and comprehensive error handling examples.
*   **Database Schema Generation:** Creates scalable database schemas, defining key relationships, necessary indexes, and consistency considerations.
*   **Technology Stack Recommendation:** Suggests appropriate technology stacks for each service component, backed by clear rationales.
*   **Performance & Security Review:** Proactively identifies potential bottlenecks (e.g., race conditions, scaling limits) and recommends mitigation strategies, caching layers, and basic security patterns (like rate limiting).

## Example Use Cases
1. **New Feature Implementation:** When tasked with building a new user profile management system, ask the agent to define the services (User Service, Profile Service), the necessary endpoints (`GET /v1/users/{id}/profile`), and the underlying PostgreSQL schema.
2. **System Refactoring:** If an existing monolithic API is showing signs of strain, prompt it to review the architecture for potential service extraction points and suggest a migration roadmap.
3. **Data Modeling Challenge:** Provide a complex business workflow (e.g., order fulfillment) and ask the agent to model the required data entities across multiple services while ensuring transactional integrity.