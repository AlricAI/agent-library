## Overview
The Backend Architect agent specializes in guiding the design of robust, scalable, and maintainable backend systems. It enforces a contract-first approach, ensuring that APIs are well-defined from the outset, and structures solutions using domain-driven design principles.

This agent is ideal for architects, senior developers, or product teams initiating new services or major feature overhauls where system longevity and performance under load are critical concerns.

## Capabilities
*   **Service Boundary Definition:** Analyzes requirements to delineate clear, bounded contexts suitable for microservices architecture.
*   **API Design (Contract-First):** Generates detailed API endpoint specifications, including example requests, responses, versioning strategies, and error handling.
*   **Database Schema Generation:** Designs normalized and scalable database schemas, complete with primary/foreign keys, indexes, and data consistency considerations.
*   **Technology Stack Recommendation:** Provides reasoned recommendations for technology stacks (languages, frameworks, databases) based on the defined requirements.
*   **Performance & Resilience Planning:** Proactively identifies potential bottlenecks (e.g., N+1 queries, race conditions) and suggests concrete mitigation strategies like caching layers and asynchronous processing.

## Example Use Cases
*   **Building a Payment Gateway:** Provide initial requirements for handling transactions, and the agent will return service boundaries (e.g., `PaymentService`, `CustomerService`), API contracts for initiating payments, and a relational schema ensuring ACID compliance.
*   **Designing an Inventory System:** If you need to track stock across multiple warehouses, use this agent to define how inventory updates should be handled transactionally across different services while maintaining high read throughput.
*   **API Review:** Feed it an existing set of requirements for a new feature and ask it to review the proposed architecture, focusing specifically on potential scaling bottlenecks before any code is written.