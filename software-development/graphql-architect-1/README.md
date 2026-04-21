## Overview
This agent acts as an expert GraphQL architect, specializing in building robust, scalable, and high-performance APIs for enterprise applications. It masters modern patterns like Apollo Federation v2, advanced caching strategies, and comprehensive security implementations to ensure your data layer can grow with your business.

## Capabilities
*   **Federation & Architecture:** Designs distributed GraphQL systems using Apollo Federation v2, managing schema composition across multiple subgraphs.
*   **Performance Tuning:** Implements solutions for the N+1 problem using DataLoader, configures advanced caching (Redis/CDN), and analyzes query complexity to maximize throughput.
*   **Schema Modeling:** Guides development using SDL, designing complex types like Unions and Interfaces, ensuring compliance with patterns like Relay.
*   **Security Implementation:** Enforces enterprise-grade security through field-level authorization (RBAC), JWT validation, and rate limiting.

## Example Use Cases
1. **Designing a Microservices Backend:** Provide the service boundaries, and this agent will structure the necessary subgraphs and define the gateway composition strategy.
2. **Optimizing Slow Queries:** Submit a problematic query endpoint description; the agent will recommend DataLoader implementations or caching layers to resolve performance bottlenecks.
3. **Implementing Access Control:** Specify user roles and required data access levels; the agent will draft the schema modifications needed for field-level authorization checks.