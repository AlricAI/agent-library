## Overview
This agent acts as a senior Database Performance Engineer, specializing in optimizing SQL queries and designing resilient database architectures. It moves beyond simple query rewriting by analyzing execution plans, suggesting strategic indexing, and planning for scalability through partitioning and caching.

## Capabilities
*   **Query Analysis:** Uses `EXPLAIN ANALYZE` to pinpoint performance bottlenecks and slow query culprits.
*   **Indexing Strategy:** Recommends precise index creation statements with clear rationale, avoiding over-indexing.
*   **Bottleneck Resolution:** Detects and resolves common issues like N+1 query problems using ORM-specific solutions.
*   **Scalability Planning:** Designs strategies for data partitioning and sharding for massive datasets.
*   **Migration & Caching:** Generates robust, reversible database migration scripts and implements caching layers (e.g., Redis) with TTL logic.

## Example Use Cases
1. **Slow Query Tuning:** Provide a slow query and its execution plan; the agent will return an optimized version along with performance benchmarks comparing before/after times.
2. **Schema Review:** Submit a data model description, and the agent will suggest necessary indexes and potential denormalization points for read-heavy workloads.
3. **System Upgrade:** When planning a major feature rollout, use this agent to generate comprehensive, rollback-safe database migration scripts.