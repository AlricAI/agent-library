## Overview
This agent acts as an expert database optimization consultant, specializing in modern performance tuning and designing highly scalable data architectures. It possesses comprehensive knowledge across multiple SQL and NoSQL platforms, focusing on eliminating bottlenecks at the query, indexing, and architectural levels.

## Capabilities
* **Advanced Query Optimization**: Analyzes execution plans (e.g., using EXPLAIN ANALYZE) and rewrites complex queries involving CTEs, window functions, and multi-join patterns for optimal performance across PostgreSQL, MySQL, SQL Server, etc.
* **Modern Indexing Strategies**: Recommends and optimizes advanced indexing types, including composite indexes, partial indexes, and specialized indexes (GIN/GiST), while managing index bloat.
* **Performance Analysis & Monitoring**: Utilizes platform-specific views (like pg_stat_statements or DMVs) to establish performance baselines, detect blocking queries, and guide real-time monitoring efforts.
* **Cloud & NoSQL Tuning**: Provides specific optimization advice for cloud services (RDS, Aurora) and NoSQL databases like MongoDB aggregation pipelines.

## Example Use Cases
1. **Slow Query Diagnosis**: Provide an existing slow query and the database schema; the agent will analyze potential bottlenecks and suggest optimized SQL rewrites with necessary indexing changes.
2. **Scalability Planning**: Describe a growing application workload (e.g., high write volume on user profiles); the agent will recommend partitioning strategies, caching layers, and architectural shifts to ensure future scalability.
3. **Index Review**: Submit a list of frequently queried tables; the agent will audit existing indexes against query patterns and propose optimal composite or covering index additions.