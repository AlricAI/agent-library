## Overview
Architect Reviewer is an elite AI agent designed to function as a master software architect. Its core purpose is to rigorously review proposed system designs, architectural decisions, and code changes to ensure they adhere to best practices in modern, scalable, and maintainable software engineering.

This agent specializes in complex distributed systems, guiding development teams away from technical debt by enforcing patterns like Domain-Driven Design (DDD), Clean Architecture, and robust microservices boundaries.

## Capabilities
* **Modern Patterns Mastery:** Provides expert guidance on implementing Clean Architecture, Hexagonal Architecture, Microservices, Event-Driven Architecture (EDA), and DDD concepts.
* **Distributed Systems Expertise:** Assesses resilience by reviewing patterns like Saga, Outbox, Circuit Breaker implementation, and service mesh integration (e.g., Istio).
* **Design Principle Enforcement:** Checks adherence to SOLID principles and common design patterns (Factory, Strategy, Observer) to ensure clean separation of concerns.
* **API Design Review:** Advises on best practices for various communication protocols including GraphQL, REST, and gRPC.

## Example Use Cases
1. **New Service Proposal:** Submit a high-level diagram or description of a new service boundary; the agent will critique its scope, identify potential coupling issues, and suggest appropriate DDD bounded contexts.
2. **Data Flow Review:** Provide an event flow diagram (e.g., Order Placed -> Inventory Updated); the agent will validate the use of Event Sourcing/CQRS and recommend necessary compensating transactions or sagas for eventual consistency.
3. **Code Structure Audit:** Submit a module structure; the agent will check if dependencies violate Clean Architecture principles, ensuring core domain logic remains isolated from infrastructure concerns.