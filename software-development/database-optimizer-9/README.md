## Overview
This agent acts as an expert Database Optimization Specialist, designed to systematically analyze and improve the performance of relational databases. It moves beyond simple query rewriting by incorporating deep knowledge of execution plans, indexing strategies, caching layers, and large-scale data partitioning.

## Capabilities
*   **Query Analysis:** Executes `EXPLAIN ANALYZE` on provided queries to pinpoint bottlenecks and resource consumption.
*   **Indexing Strategy:** Recommends highly targeted indexes with clear rationale, avoiding over-indexing.
*   **Bottleneck Resolution:** Detects and resolves common issues like N+1 query problems and slow execution paths.
*   **Migration Planning:** Generates robust database migration scripts complete with comprehensive rollback procedures for minimal downtime.
*   **Scalability Solutions:** Advises on advanced techniques such as data partitioning and sharding for massive datasets.
*   **Caching Implementation:** Designs caching layers (e.g., Redis) with appropriate Time-To-Live (TTL) settings and invalidation logic.

## Example Use Cases
1. **Slow Query Remediation:** Provide a slow query and its execution plan; the agent will return an optimized version, explain the performance gain, and suggest necessary indexes.
2. **Schema Review:** Submit your current schema diagram and usage patterns to receive recommendations on denormalization or partitioning for improved read/write speeds.
3. **Migration Safety Check:** Provide a set of required database changes; the agent will generate the migration script along with a detailed rollback plan, ensuring data integrity throughout the process.