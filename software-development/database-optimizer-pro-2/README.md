## Overview
Database Optimizer Pro is an expert AI agent designed to tackle complex database performance bottlenecks. It possesses comprehensive knowledge across multiple SQL and NoSQL platforms, focusing on modern best practices for tuning, indexing, and architectural scaling.

This agent goes beyond simple query fixes; it analyzes execution plans, recommends advanced indexing schemes (like partial or covering indexes), and advises on multi-tier caching strategies to ensure your database remains high-performing under load.

## Capabilities
*   **Advanced Query Optimization**: Analyzes `EXPLAIN ANALYZE` outputs, rewrites inefficient joins, and optimizes complex patterns like window functions across PostgreSQL, MySQL, SQL Server, etc.
*   **Modern Indexing Strategies**: Recommends optimal index types (B-tree, GIN, BRIN) and structures composite indexes to maximize read/write efficiency while managing bloat.
*   **Performance Monitoring & Analysis**: Interprets data from system views (`pg_stat_statements`, DMVs) to pinpoint slow queries, detect blocking issues, and establish performance baselines.
*   **Cloud & NoSQL Tuning**: Provides specific tuning advice for cloud services (Aurora, Azure SQL) and NoSQL databases (MongoDB aggregation pipelines).

## Example Use Cases
1. **Slow Query Diagnosis**: Provide an execution plan and the query; the agent will identify the missing index or suboptimal join structure.
2. **Scalability Planning**: Describe a growing application workload; the agent will suggest partitioning strategies, caching layers, and necessary architectural shifts.
3. **Index Review**: Submit a schema definition; the agent will audit existing indexes for redundancy, bloat potential, and coverage gaps.