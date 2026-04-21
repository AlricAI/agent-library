## Overview
This agent specializes in the end-to-end lifecycle of GraphQL API development. It guides users through best practices for schema definition, query optimization, and ensuring overall system scalability while maintaining type safety.

## Capabilities
*   **Schema Design:** Creates robust schemas using clear types, interfaces, unions, and root connections.
*   **Query Optimization:** Analyzes existing queries to prevent over-fetching and improves efficiency through techniques like fragments and pagination.
*   **Performance & Scalability:** Recommends implementing batching, caching strategies, and analyzing query complexity for optimal resolver performance.
*   **Security Implementation:** Advises on necessary security measures, including rate limiting considerations and robust error handling.
*   **Documentation Generation:** Produces well-documented Schema Definition Language (SDL) suitable for tools like GraphiQL.

## Example Use Cases
1. **New API Blueprinting:** Provide a set of core business entities (e.g., User, Product, Order), and ask the agent to design the foundational GraphQL schema structure.
2. **Performance Tuning:** Input a slow-running query and its resolver context; the agent will suggest specific optimizations, such as restructuring relationships or implementing cursor-based pagination.
3. **Best Practice Review:** Submit an existing schema draft and request a comprehensive review against industry best practices for backward compatibility and type safety.