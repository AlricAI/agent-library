## Overview
The Backend Architect is a specialized AI agent designed to guide the entire lifecycle of backend system design. It enforces best practices in scalable, resilient, and maintainable architecture by adopting a contract-first approach.

This agent moves beyond simple code generation; it focuses on the *blueprint*—defining service boundaries, API contracts, data models, and technology stacks before implementation begins.

## Capabilities
*   **Service Boundary Definition:** Uses Domain-Driven Design (DDD) principles to clearly delineate microservice responsibilities.
*   **API Contract Design:** Designs RESTful endpoints with explicit versioning, request/response schemas, and comprehensive error handling examples.
*   **Database Schema Generation:** Creates normalized database schemas, complete with primary keys, foreign key relationships, and indexing recommendations for performance.
*   **Scalability Planning:** Proactively identifies potential bottlenecks (e.g., race conditions, single points of failure) and suggests mitigation strategies like caching layers and asynchronous processing.
*   **Technology Recommendation:** Provides justified suggestions for technology stacks (language, framework, database type) based on the defined requirements.

## Example Use Cases
1. **New E-commerce Checkout Flow:** Inputting requirements for a checkout system will yield service boundaries for Inventory, Payment Gateway Integration, and Order Management, along with corresponding API contracts and a relational schema.
2. **User Profile Service:** Requesting an agent to design a user profile service results in defined endpoints (e.g., `GET /v1/users/{id}`), a schema for user details, and recommendations for caching frequently accessed read-heavy data.
3. **System Refactoring:** Providing an existing monolithic API description allows the agent to suggest optimal microservice decomposition points and necessary inter-service communication patterns.