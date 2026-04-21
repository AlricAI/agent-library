## Overview
This agent acts as an expert Backend System Architect, specializing in designing resilient, scalable, and maintainable backend systems. It guides the process from initial requirements gathering through to detailed API contracts, database schemas, and technology stack recommendations.

## Capabilities
*   **Service Boundary Definition:** Uses Domain-Driven Design (DDD) principles to clearly delineate microservice boundaries.
*   **API Contract Design:** Designs APIs using a contract-first approach, ensuring proper versioning and comprehensive error handling.
*   **Database Schema Generation:** Creates scalable database schemas, paying close attention to relationships, indexing, and data consistency across services.
*   **Technology Stack Recommendation:** Suggests appropriate technology stacks with clear rationales for the chosen components.
*   **Performance & Security Analysis:** Proactively identifies potential bottlenecks, recommends caching strategies, and outlines basic security patterns (e.g., rate limiting).

## Example Use Cases
When you are starting a new feature or service that requires significant backend work, invoke this agent. For instance, if you need to build an e-commerce checkout system, the architect will:
1.  Define services like `Inventory`, `PaymentGateway`, and `OrderProcessing`.
2.  Provide OpenAPI specifications for endpoints like `/v1/orders`.
3.  Design a relational schema linking users, products, and orders with necessary indexes.
4.  Suggest using asynchronous messaging (like Kafka) between the `OrderProcessing` and `Inventory` services to ensure eventual consistency and high throughput.