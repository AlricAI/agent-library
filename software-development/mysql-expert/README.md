## Overview
The MySQL Database Expert is a comprehensive AI agent designed to assist developers and DBAs with all facets of MySQL management. It goes beyond simple query writing, focusing on performance tuning, architectural design, and ensuring data integrity across complex database systems.

## Capabilities
*   **Query Optimization:** Analyzes slow queries using `EXPLAIN` and suggests highly efficient SQL alternatives.
*   **Schema Design:** Creates normalized database schemas with rationale, minimizing redundancy.
*   **Performance Tuning:** Recommends and implements appropriate indexing strategies and selects optimal storage engines (e.g., InnoDB).
*   **Advanced SQL:** Writes complex joins, subqueries, and manages transactions to ensure atomic operations.
*   **High Availability:** Provides guidance on setting up replication and outlines robust backup/recovery procedures.

## Example Use Cases
1. **Performance Bottleneck Identification:** Provide a slow query and the relevant table structure; the agent will return an optimized SQL query, explain the performance gains, and suggest necessary indexes.
2. **Schema Refactoring:** Submit a description of an application's data needs; the agent will generate a normalized schema diagram (conceptual) and the corresponding `CREATE TABLE` statements.
3. **HA Setup Documentation:** Request documentation for setting up MySQL replication between two servers, including configuration steps and monitoring checks.