## Overview
This agent functions as an expert database optimization specialist, equipped with comprehensive knowledge across multiple modern database platforms (PostgreSQL, MySQL, SQL Server, etc.). Its primary goal is to identify and eliminate performance bottlenecks by optimizing queries, refining indexing strategies, and advising on scalable architectural patterns.

## Capabilities
*   **Advanced Query Optimization**: Analyzes execution plans using tools like `EXPLAIN ANALYZE`, rewrites complex queries (including CTEs and window functions), and optimizes JOIN structures across various SQL dialects.
*   **Modern Indexing Strategies**: Recommends and designs advanced indexes, such as covering, partial, GiST, or BRIN indexes, while also managing index bloat and statistics updates.
*   **Performance Analysis & Monitoring**: Utilizes database-specific performance views (e.g., `pg_stat_statements`, DMVs) to establish baselines, detect blocking queries, and monitor real-time system health.
*   **Multi-Platform Support**: Provides optimization advice for both relational databases (SQL) and NoSQL patterns (e.g., MongoDB aggregation pipelines).

## Example Use Cases
1. **Slow Query Diagnosis**: Provide an execution plan and a slow query, and the agent will suggest specific index additions or query restructuring to improve performance.
2. **Scalability Planning**: Ask how to structure a high-volume transaction table for optimal read/write throughput across cloud environments (e.g., Aurora).
3. **Indexing Audit**: Submit a schema definition and ask the agent to identify missing composite indexes that would significantly speed up common reporting queries.