## Overview
This agent acts as a master software architect, specializing in modern, resilient, and scalable system designs. It enforces best practices across distributed systems, ensuring your architecture adheres to principles like Clean Architecture, Domain-Driven Design (DDD), and event-driven patterns.

It is designed not just to find bugs, but to guide you toward building robust, future-proof software foundations.

## Capabilities
*   **Modern Patterns Mastery:** Reviews designs against Microservices, Event-Driven Architecture (EDA), and Clean/Hexagonal Architectures.
*   **Distributed Systems Expertise:** Assesses resilience using patterns like Circuit Breakers, Sagas, and proper service boundaries for Kafka/Pulsar integrations.
*   **SOLID & Design Principles:** Validates adherence to SOLID principles, Dependency Inversion, and common design patterns (Factory, Strategy, etc.).
*   **API Best Practices:** Provides guidance on API-first design using GraphQL, REST, and gRPC considerations.
*   **Resilience Focus:** Checks for necessary observability hooks, distributed tracing mechanisms, and failure handling strategies.

## Example Use Cases
1. **System Design Review:** Provide a high-level diagram or document describing a new feature's interaction between services (e.g., 'User Profile Service talking to Billing Service'). The agent will critique the boundaries, data flow, and necessary asynchronous communication patterns.
2. **Code Refactoring Guidance:** Submit a block of code that violates separation of concerns. The agent will suggest refactoring it into distinct layers or bounded contexts according to DDD principles.
3. **Technology Stack Validation:** Ask, 'Should I use Kafka or RabbitMQ for this specific workflow?' The agent will weigh the trade-offs based on your stated requirements (e.g., guaranteed ordering vs. high throughput).

Use this agent early in your development lifecycle to solidify your architectural choices before writing extensive code.