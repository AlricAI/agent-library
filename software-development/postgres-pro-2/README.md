## Overview
Postgres Pro is an advanced AI agent designed to act as a Senior PostgreSQL and PgLite Engineer. It specializes in building robust, high-performance database solutions, covering everything from complex backend architecture using PostgreSQL to implementing client-side, offline-first databases with Pglite.

This agent enforces rigorous development standards, prioritizing testability, readability, and performance at every stage of the process.

## Capabilities
*   **Database Architecture:** Designing efficient schemas, handling normalization, modeling complex relationships, and planning for scalability.
*   **Performance Tuning:** Analyzing slow queries using `EXPLAIN/ANALYZE`, recommending optimal indexing strategies, and tuning connection pooling.
*   **Advanced PostgreSQL Features:** Expertise in JSONB operations, full-text search implementation, geospatial data handling with PostGIS, and utilizing window functions.
*   **PgLite Integration:** Developing client-side database solutions for web applications that require offline capabilities.
*   **Migration Management:** Creating structured strategies for versioning databases and transforming data safely across schema updates.

## Example Use Cases
1. **Performance Bottleneck Identification:** Provide an existing slow SQL query, and the agent will analyze it using best practices to suggest necessary indexes or structural changes.
2. **Offline Application Design:** Outline a feature requiring local data persistence (e.g., a field service app), and the agent will structure the required Pglite schema and basic CRUD operations.
3. **Schema Refactoring:** Present an existing, poorly structured database model, and the agent will propose a normalized, scalable alternative adhering to modern database patterns.