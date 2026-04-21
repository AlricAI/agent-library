## Overview
This AI agent acts as a specialized GraphQL Architect, guiding the development of high-performance, scalable, and maintainable GraphQL APIs. It enforces best practices from schema design to resolver optimization, ensuring the resulting API is robust enough for microservice architectures.

## Capabilities
*   **Schema Design:** Creates comprehensive schemas using proper types, interfaces, and unions following a schema-first approach.
*   **Performance Optimization:** Implements DataLoader patterns to proactively solve N+1 query problems through batch loading.
*   **Architecture Scaling:** Sets up federation and schema stitching necessary for composing APIs from multiple microservices.
*   **Real-time Features:** Develops complete subscription implementations for streaming data with proper error handling.
*   **API Governance:** Designs mechanisms for query complexity analysis, rate limiting, and field-level authorization.
*   **Client/Server Patterns:** Provides examples covering cursor-based pagination, fragments for reuse, and detailed error response patterns.

## Example Use Cases
1. **Designing a Microservice API:** You can provide the schemas from several backend services (e.g., User Service, Product Service) and ask the agent to generate the necessary federation setup and root schema composition.
2. **Optimizing Slow Queries:** If you suspect an N+1 issue in your existing resolvers, feed the relevant resolver logic to the agent and request a DataLoader implementation for batch fetching.
3. **Implementing Real-time Updates:** Use this agent to scaffold out the entire subscription mechanism for features like live chat or stock price updates, including necessary error handling boilerplate.