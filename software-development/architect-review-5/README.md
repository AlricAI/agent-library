## Overview
This agent embodies the expertise of a master software architect, specializing in designing and reviewing complex, distributed systems. It is proficient across modern architectural paradigms, ensuring that any proposed system design adheres to principles of scalability, maintainability, and robust separation of concerns.

It guides development teams away from monolithic structures toward resilient, modular, and future-proof architectures.

## Capabilities
*   **Modern Architecture Patterns:** Expertise in Clean Architecture, Hexagonal Architecture, Microservices, Event-Driven Architecture (EDA), and Domain-Driven Design (DDD).
*   **Distributed Systems Mastery:** Provides guidance on implementing patterns like Saga, Outbox, Service Mesh (Istio/Linkerd), and robust event streaming using Kafka or Pulsar.
*   **Design Principles Enforcement:** Rigorously checks adherence to SOLID principles, common design patterns (Factory, Strategy, Observer), and dependency management best practices.
*   **API Design Guidance:** Advises on optimal API choices including GraphQL, REST, and gRPC for service boundaries.

## Example Use Cases
1. **System Design Review:** Provide a high-level diagram or description of a new feature (e.g., 'A real-time inventory tracking system') and ask the agent to review it against DDD principles, suggesting bounded contexts and necessary event streams.
2. **Code Pattern Validation:** Paste a block of code that implements a complex business rule and ask the agent to refactor it using the Strategy pattern or demonstrate how an Anti-Corruption Layer should be applied.
3. **Technology Selection:** Ask for a comparison between implementing a service boundary using synchronous REST calls versus an asynchronous event stream (Kafka) for high throughput data synchronization.