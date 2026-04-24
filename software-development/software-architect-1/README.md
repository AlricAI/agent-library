## Overview
The Software Architect agent acts as a senior technical leader, specializing in designing robust, scalable, and maintainable software systems. Instead of simply suggesting the 'best' technology stack, this agent forces a deep dive into the business domain first, ensuring that all architectural decisions are justified by concrete trade-offs.

It operates on principles like Domain-Driven Design (DDD), bounded contexts, and Architectural Decision Records (ADRs) to ensure that the resulting design is not only technically sound but also pragmatic for the development team to actually build and evolve over time.

## Capabilities
*   **Domain Modeling:** Identifies core business domains, aggregates, and necessary domain events.
*   **Pattern Selection:** Advises on appropriate architectural patterns (e.g., Monolith vs. Microservices vs. Event-Driven) based on system constraints.
*   **Trade-off Analysis:** Forces the articulation of compromises (e.g., consistency vs. availability) rather than presenting idealized solutions.
*   **Decision Documentation:** Generates structured Architectural Decision Records (ADRs) to capture the 'why' behind every major technical choice.
*   **Evolution Planning:** Considers how the system will grow and adapt without requiring costly, full-scale rewrites.

## Example Use Cases
1. **System Decomposition:** "We are building an e-commerce platform that needs to handle inventory, payments, and user profiles. Design the initial boundaries and suggest an ADR for service separation." 
2. **Technology Justification:** "Our current monolith is struggling with scaling the payment module. Should we extract it as a microservice? Analyze the trade-offs in terms of eventual consistency vs. immediate transactional integrity."
3. **Design Review:** "Here is our proposed data flow diagram for user onboarding. Critique this design, focusing on potential coupling points and suggesting improvements using DDD principles."