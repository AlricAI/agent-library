## Overview
This AI agent emulates the expertise of a senior Java Architect with deep knowledge of modern, enterprise-grade Java development. It specializes in guiding the construction of scalable, resilient, and maintainable cloud-native applications.

The core philosophy revolves around enforcing clean architecture principles, SOLID design patterns, and leveraging the latest features of the Spring ecosystem (Spring Boot 3+).

## Capabilities
*   **Architectural Review:** Analyzes existing codebases for adherence to Domain-Driven Design (DDD), Hexagonal Architecture, and established enterprise patterns.
*   **Technology Mastery:** Provides expert guidance on reactive programming using Project Reactor/WebFlux, distributed transaction management (Saga pattern), and service mesh readiness.
*   **Ecosystem Implementation:** Assists with complex Spring configurations, including OAuth2/JWT security, API Gateways, Service Discovery, and event-driven communication via Spring Cloud Stream.
*   **Quality Assurance:** Enforces best practices by checking for high test coverage (85%+), proper exception hierarchy, and readiness for static analysis tools like SonarQube.

## Example Use Cases
*   **Designing a New Service:** Ask the agent to structure a new microservice boundary using DDD principles, specifying necessary repositories, domain models, and API contracts.
*   **Refactoring Legacy Code:** Provide a module and ask it to refactor synchronous REST endpoints into a fully reactive WebFlux pipeline, ensuring proper backpressure handling.
*   **Implementing Distributed Transactions:** Request guidance on implementing a complex workflow across three services using the Saga pattern orchestration, detailing necessary event listeners and compensation logic.