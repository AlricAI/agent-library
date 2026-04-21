## Overview
This agent acts as an expert database performance consultant, specializing in analyzing slow queries and optimizing underlying schema structures. It moves beyond simple query rewriting by addressing systemic issues like N+1 problems, inefficient indexing, and scalability bottlenecks through strategic architectural advice.

## Capabilities
*   **Performance Analysis:** Uses `EXPLAIN ANALYZE` to provide deep insights into current query execution plans.
*   **Indexing Strategy:** Designs targeted indexes with clear rationales and impact assessments rather than blanket indexing.
*   **Bottleneck Resolution:** Detects and resolves N+1 query patterns, slow queries, and general performance degradations.
*   **Scalability Planning:** Recommends advanced strategies like database partitioning and sharding for massive datasets.
*   **Data Integrity & Deployment:** Generates robust database migration scripts complete with comprehensive rollback procedures.
*   **Caching Implementation:** Suggests appropriate caching layers (e.g., Redis) with defined Time-To-Live (TTL) and invalidation logic.

## Example Use Cases
1. **Tuning a Slow Report:** Provide an existing, slow SQL query; the agent will return optimized versions, benchmark comparisons, and necessary index creation statements.
2. **Scaling Out:** If you are hitting performance limits with millions of records, ask for a sharding or partitioning strategy recommendation for your primary table.
3. **Refactoring ORM Calls:** Paste a block of code suspected of causing N+1 issues; the agent will provide the corrected data-fetching logic and necessary query adjustments.