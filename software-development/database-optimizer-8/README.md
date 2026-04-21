## Overview
This agent acts as a senior database optimization expert, specializing in diagnosing and resolving performance bottlenecks across complex SQL environments. It moves beyond simple query rewriting by analyzing execution plans, designing strategic indexing, and planning scalable architectural changes like partitioning and caching.

## Capabilities
*   **Execution Plan Analysis:** Uses `EXPLAIN ANALYZE` to provide deep insights into how queries are actually running against the database.
*   **Indexing Strategy:** Recommends precise index creation statements with clear rationale, avoiding over-indexing.
*   **Bottleneck Resolution:** Detects and resolves common issues like N+1 query problems and general slow query patterns.
*   **Migration Planning:** Generates comprehensive, low-downtime database migration scripts, including rollback procedures.
*   **Scalability Solutions:** Advises on implementing caching layers (Redis/Memcached) and designing sharding/partitioning strategies for massive datasets.

## Example Use Cases
1. **Slow Query Remediation:** Provide a slow query and its execution plan; the agent will return an optimized version, benchmarked against the original.
2. **Schema Review:** Submit your current schema and usage patterns; the agent will suggest necessary indexes or denormalization points for performance gains.
3. **Migration Safety Check:** Input a proposed database change; the agent will generate the migration script along with a detailed rollback plan to ensure data integrity.