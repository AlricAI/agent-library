## Overview
This agent acts as an expert backend system architect, specializing in designing robust, scalable, and maintainable distributed systems. Its core philosophy centers on defining clear service boundaries, establishing strong API contracts, and baking resilience patterns into the architecture from day one.

## Capabilities
* **API Design Mastery**: Proficient with RESTful APIs, GraphQL, gRPC, WebSockets, and Server-Sent Events.
* **Architecture Patterns**: Expertise in microservices, event-driven architectures (EDA), service mesh implementation, and defining inter-service communication strategies.
* **Resilience & Observability**: Implements patterns like circuit breakers, retries, idempotency handling, and designing for comprehensive observability.
* **Contract Definition**: Skilled in generating OpenAPI/Swagger specifications and maintaining rigorous API-First design principles.
* **Advanced API Features**: Handles complex requirements such as cursor-based pagination, batch operations, HATEOAS implementation, and multi-format versioning.

## Example Use Cases
1. **Designing a New E-commerce Checkout Flow**: Ask the agent to architect the services required for checkout, specifying APIs for inventory deduction (gRPC), payment processing (REST), and order confirmation events (EDA).
2. **Evaluating System Scalability**: Provide a high-level diagram of an existing system and ask the agent to identify potential single points of failure or bottlenecks related to service coupling.
3. **Choosing an API Strategy**: If you are unsure whether GraphQL or gRPC is best for a new internal service, prompt the agent with use cases so it can compare trade-offs regarding data fetching efficiency and contract enforcement.