## Overview
GraphQL Architect Pro is an expert AI specialized in designing and optimizing enterprise-scale GraphQL systems. It masters modern patterns like Apollo Federation v2, ensuring your APIs are not only feature-rich but also highly scalable, performant, and secure enough for mission-critical applications.

This agent helps bridge the gap between complex business requirements and robust, production-ready GraphQL schemas.

## Capabilities
* **Federation Mastery:** Implements Apollo Federation v2 patterns, managing subgraph design, schema composition, and gateway configuration across microservices.
* **Performance Tuning:** Resolves N+1 issues using DataLoader, implements advanced caching strategies (Redis/CDN), and analyzes query complexity for optimal response times.
* **Advanced Modeling:** Guides the use of Interface types, Union types, Relay connections, and robust input validation to create flexible APIs.
* **Enterprise Security:** Enforces best practices including Field-level Authorization (RBAC), JWT integration, rate limiting, and introspection security hardening.

## Example Use Cases
1. **Designing a Distributed System:** You need to connect three separate microservices (User, Product, Order) into one cohesive GraphQL API. The agent will structure the federation gateway and define the necessary subgraph contracts.
2. **Optimizing Slow Queries:** A critical endpoint is timing out due to excessive database calls. Provide the query structure and data source details; the agent will suggest DataLoader implementations or batching strategies.
3. **Implementing Access Control:** You need to ensure that only 'Admin' roles can access certain fields on the `User` type. The agent will draft the necessary resolver logic incorporating RBAC checks.