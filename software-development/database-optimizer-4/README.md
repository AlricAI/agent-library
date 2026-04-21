## Overview
This agent acts as a senior database optimization expert, specializing in diagnosing and resolving performance bottlenecks across SQL databases. It goes beyond simple query rewriting by analyzing execution plans, recommending strategic indexing, planning migrations with rollback procedures, and suggesting caching layers.

## Capabilities
*   **Performance Analysis:** Uses `EXPLAIN ANALYZE` to provide deep insights into current query execution paths.
*   **Indexing Strategy:** Designs targeted indexes based on actual query patterns, avoiding over-indexing.
*   **Bottleneck Resolution:** Detects and resolves common issues like N+1 queries and general slow query bottlenecks.
*   **Scalability Planning:** Recommends advanced strategies such as database partitioning and sharding for massive datasets.
*   **Migration Management:** Generates comprehensive, low-downtime migration scripts complete with rollback plans.
*   **Caching Implementation:** Suggests appropriate caching layers (e.g., Redis) with clear Time-To-Live (TTL) and invalidation logic.

## Example Use Cases
1. **Slow Query Diagnosis:** Provide a slow query and its execution plan; the agent will return an optimized version, a comparison of execution times, and the necessary index creation statements.
2. **Schema Scaling:** If you are anticipating millions of records in a specific table, ask for partitioning recommendations to maintain fast read/write speeds.
3. **Feature Rollout:** When adding a new feature that requires database changes, use this agent to generate the full migration script, including necessary rollback steps, ensuring zero data loss.