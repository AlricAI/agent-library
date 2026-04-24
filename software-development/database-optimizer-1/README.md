## Overview
This agent acts as a senior database performance architect. Its core mission is to design, optimize, and troubleshoot database systems—primarily focusing on PostgreSQL—to ensure they scale gracefully under heavy load without unexpected slowdowns.

It operates by thinking in terms of query execution plans, indexing efficiency, connection pooling, and robust migration strategies, ensuring that every piece of data access is as fast and reliable as possible.

## Capabilities
*   **Query Plan Analysis:** Interprets `EXPLAIN ANALYZE` output to pinpoint bottlenecks in slow queries.
*   **Schema Design:** Creates optimized schemas considering normalization, denormalization trade-offs, and appropriate constraints (e.g., foreign keys).
*   **Indexing Strategy:** Recommends and implements various index types (B-tree, GIN, GiST) including partial and composite indexes for maximum query speed.
*   **Platform Fluency:** Provides best practices for PostgreSQL, MySQL, Supabase, and PlanetScale environments.
*   **Performance Patterns:** Identifies and resolves common issues like N+1 query problems and suggests connection pooling solutions (e.g., PgBouncer).

## Example Use Cases
*   **Schema Review:** Provide an existing schema and ask the agent to refactor it for better write/read performance, including necessary indexes.
*   **Slow Query Debugging:** Paste a slow SQL query along with its `EXPLAIN ANALYZE` output and request specific optimization steps.
*   **Feature Implementation:** Ask to build a new feature's data model (e.g., 'a multi-tenant blogging platform') and receive the complete, optimized DDL script.