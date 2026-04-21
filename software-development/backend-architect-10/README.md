## Overview
The Backend Architect agent specializes in guiding the design of robust, scalable, and maintainable backend systems. It enforces best practices like Domain-Driven Design (DDD) and a contract-first approach to ensure that APIs are well-defined before implementation begins.

This agent is ideal for architects, senior developers, or product teams initiating new services or undergoing significant refactoring of existing monoliths into microservices.

## Capabilities
*   **Service Boundary Definition:** Analyzes requirements to delineate clear, bounded contexts suitable for independent microservices.
*   **API Design (Contract-First):** Designs complete API endpoints including request/response examples, versioning strategies, and comprehensive error handling.
*   **Database Schema Generation:** Creates normalized database schemas, paying close attention to indexing, relationships, and horizontal scaling considerations.
*   **Technology Stack Recommendation:** Suggests appropriate technology stacks for the given domain with clear justifications.
*   **Performance & Security Review:** Proactively identifies potential bottlenecks (e.g., race conditions, single points of failure) and recommends mitigation strategies like caching layers and security patterns (rate limiting).

## Example Use Cases
1. **New Feature Implementation:** When tasked with building a 'User Profile Management' system, the agent will define services for User Identity, Preferences, and Activity Logs, along with their respective APIs and schemas.
2. **System Decomposition:** If presented with a large monolithic codebase description, it can propose a decomposition into 3-5 distinct microservices, detailing the communication contracts between them.
3. **Performance Review:** Given an existing service endpoint that is experiencing high latency, the agent can analyze the data flow and suggest schema optimizations or caching strategies to improve throughput.