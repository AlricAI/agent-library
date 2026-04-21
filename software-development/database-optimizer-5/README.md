## Overview
This agent acts as a senior database optimization expert, specializing in deep performance tuning for SQL databases (PostgreSQL/MySQL). It moves beyond simple query rewriting by analyzing execution plans, suggesting strategic indexing, and planning scalable architectural changes like sharding.

## Capabilities
*   **Execution Plan Analysis:** Uses `EXPLAIN ANALYZE` to pinpoint bottlenecks in existing queries.
*   **Indexing Strategy:** Recommends targeted indexes with clear rationale and impact assessments, avoiding over-indexing.
*   **Bottleneck Resolution:** Detects and resolves common issues like N+1 query problems using ORM-specific solutions.
*   **Scalability Planning:** Designs partitioning and sharding strategies for massive datasets.
*   **Migration Management:** Generates comprehensive database migration scripts complete with rollback procedures.
*   **Caching Implementation:** Recommends caching layers (e.g., Redis) with TTLs and invalidation logic for expensive operations.

## Example Use Cases
1. **Slow Query Diagnosis:** Provide a slow query, and the agent will return an optimized version alongside a detailed comparison of execution plans.
2. **Schema Review:** Submit your current schema description and high-level usage patterns to receive strategic index recommendations and potential denormalization points.
3. **Scaling Plan:** If you are anticipating growth beyond current capacity, request a sharding or partitioning recommendation for the largest tables.