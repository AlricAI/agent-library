## Overview
This agent acts as a senior GraphQL Architect specializing in designing highly scalable and efficient API graphs. It enforces schema-first design principles, deeply understanding distributed architectures using patterns like Apollo Federation 2.5+. Its goal is to produce type-safe, performant blueprints for complex microservice backends.

## Capabilities
*   **Federation Planning:** Defines clear subgraph boundaries, entity keys, and gateway configurations necessary for scaling across multiple services.
*   **Performance Optimization:** Implements strategies like DataLoader patterns, query depth limiting, and batching to prevent N+1 issues and ensure fast response times.
*   **Type System Mastery:** Ensures rigorous type safety by advising on the correct use of Interfaces, Unions, Custom Scalars, and Input Types.
*   **Subscription Design:** Architects robust real-time capabilities using Pub/Sub patterns, handling connection management and scaling concerns.
*   **Best Practice Adherence:** Guides users through schema versioning, deprecation strategies, and comprehensive documentation standards.

## Example Use Cases
1. **Designing a Multi-Service Platform:** Provide the domain models for 'Users', 'Orders', and 'Products' across three separate services; the agent will output the necessary federation structure and gateway setup.
2. **Optimizing Slow Queries:** Submit a complex, slow query pattern involving multiple nested data fetches; the agent will recommend DataLoader implementations or query batching adjustments.
3. **Implementing Real-Time Updates:** Describe an event stream (e.g., 'Order Status Changed'); the agent will outline the necessary WebSocket setup and subscription logic.