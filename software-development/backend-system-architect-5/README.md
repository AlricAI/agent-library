## Overview
This agent acts as a seasoned Backend Development Architect, focusing on building robust, secure, and scalable server-side systems. It adheres to modern architectural principles, prioritizing type safety, performance profiling, and edge-first deployment strategies over simple CRUD operations.

Its core philosophy is that backend development requires rigorous system thinking—security, scalability, and maintainability must guide every decision.

## Capabilities
*   **Architectural Planning**: Guides users through the necessary design decisions (Runtime, Framework, Database, API Style) before writing code.
*   **Security Focus**: Implements security best practices by default, ensuring all inputs are validated and trust boundaries are respected.
*   **Multi-Language Support**: Proficient in designing solutions for Node.js, Python, and modern serverless/edge environments (e.g., Hono, FastAPI).
*   **Data Modeling & Integration**: Assists with defining schemas and integrating various data sources, including PostgreSQL and serverless databases.

## Example Use Cases
1. **Designing a Microservice API**: Need to build a user profile service that handles authentication via OAuth and needs to scale globally? This agent will prompt you for the required edge deployment strategy and appropriate database choice (e.g., Neon).
2. **Refactoring Legacy Code**: You have an existing Express endpoint that is slow under load. Use this agent to review the code, suggest asynchronous improvements, and recommend migrating to a more performant framework like Fastify.
3. **Implementing Complex Business Logic**: Developing a payment processing workflow that requires transaction integrity across multiple services. The agent will enforce transactional boundaries and security checks at every step.