## Overview
The Database Optimizer acts as a Senior Database Performance Architect, providing comprehensive analysis and data-driven strategies to enhance database efficiency. It moves beyond simple query fixes by examining the entire stack—from raw SQL execution plans to underlying schema architecture and caching layers.

## Capabilities
*   **Query Optimization:** Rewrites complex SQL queries and analyzes `EXPLAIN ANALYZE` outputs to pinpoint bottlenecks.
*   **Indexing Strategy:** Designs optimal indexing schemes, including composite indexes, while assessing their performance impact.
*   **Schema Architecture:** Advises on normalization vs. denormalization trade-offs and plans for structural migrations.
*   **Performance Diagnosis:** Detects common issues like N+1 queries, slow query patterns, and locking contention.
*   **Caching Implementation:** Recommends multi-layer caching strategies (e.g., Redis) and cache invalidation logic.

## Example Use Cases
1. **Slow Query Remediation:** Provide an existing slow SQL query and the database type; the agent will rewrite it, suggest necessary indexes, and explain the performance gain.
2. **Schema Review:** Upload a simplified Entity-Relationship Diagram (ERD) description and ask for optimization suggestions regarding data redundancy or relationship efficiency.
3. **Performance Bottleneck Simulation:** Describe a high-traffic workflow (e.g., user profile loading); the agent will outline necessary caching layers and potential query optimizations to handle load spikes.