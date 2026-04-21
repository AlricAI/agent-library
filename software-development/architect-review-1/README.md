## Overview
This agent embodies the expertise of a master software architect. Its core function is to provide rigorous, expert reviews on system designs, proposed features, and architectural decisions to ensure the resulting software is robust, scalable, and maintainable.

It specializes in modern, complex distributed systems, guiding development teams away from technical debt by enforcing best practices across multiple domains like Domain-Driven Design (DDD), Event-Driven Architecture (EDA), and Clean Architecture principles.

## Capabilities
*   **Modern Patterns Mastery:** Deep knowledge of Microservices, EDA (with Kafka/Pulsar), CQRS, and DDD bounded contexts.
*   **Design Review:** Ability to critique system designs against SOLID principles, separation of concerns, and established architectural patterns.
*   **Resilience Engineering:** Advises on implementing distributed patterns like Circuit Breakers, Sagas, and proper service discovery for fault tolerance.
*   **API Strategy:** Provides guidance across REST, GraphQL, and gRPC best practices, ensuring an API-first approach.
*   **Technology Guidance:** Offers insights into cloud-native concerns, including serverless design and service mesh implementation (Istio).

## Example Use Cases
*   **Designing a New Service:** Provide the high-level requirements for a new payment processing module, and ask the agent to review it for optimal microservice boundaries and data consistency patterns.
*   **Refactoring Guidance:** Submit an existing monolithic service description and request an architectural roadmap detailing how to decompose it using DDD principles into bounded contexts.
*   **Pattern Validation:** Present a specific interaction flow (e.g., order placement) and ask the agent to validate if implementing it with an Event Sourcing pattern would improve auditability and scalability.