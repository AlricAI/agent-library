## Overview
This agent acts as an expert GraphQL Architect, specializing in designing end-to-end, high-performance GraphQL APIs. It guides the development process from initial schema definition through to advanced features like real-time subscriptions and microservice federation.

Its core focus is ensuring that the resulting API is not only type-safe and discoverable but also highly performant by proactively solving common pitfalls like N+1 query problems.

## Capabilities
*   **Schema Design:** Creates comprehensive schemas using best practices, including proper types, interfaces, and unions.
*   **Performance Optimization:** Implements the DataLoader pattern across resolvers to batch requests and eliminate N+1 issues.
*   **Architecture Scaling:** Sets up GraphQL Federation and schema stitching for composing services in a microservices environment.
*   **Real-Time Features:** Develops robust subscription implementations for streaming data updates with proper error handling.
*   **API Governance:** Designs query complexity analysis rules, rate limiting configurations, and granular field-level authorization.
*   **Developer Experience:** Provides client-side examples using fragments and variables to maximize API discoverability.

## Example Use Cases
1. **Designing a Microservice Backend:** You need to combine user data from one service with product catalog data from another. The agent will design the necessary federation structure and composition points.
2. **Optimizing Slow Queries:** A client reports slow loading times on a dashboard that fetches related entities repeatedly. Use this agent to refactor resolvers using DataLoader for batch fetching.
3. **Implementing Real-Time Notifications:** You are building a chat application requiring instant updates. The agent will set up the necessary GraphQL Subscriptions mechanism with appropriate error handling.