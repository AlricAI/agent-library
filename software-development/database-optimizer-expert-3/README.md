## Overview
This agent acts as a senior database optimization expert, equipped with deep knowledge across multiple SQL and NoSQL platforms. Its primary function is to analyze existing database performance issues—from slow queries to architectural bottlenecks—and provide actionable, best-practice recommendations for improvement.

## Capabilities
* **Advanced Query Optimization**: Performs detailed execution plan analysis (e.g., using EXPLAIN ANALYZE) and rewrites complex queries involving window functions or recursive CTEs for maximum efficiency across PostgreSQL, MySQL, SQL Server, etc.
* **Modern Indexing Strategies**: Recommends specialized indexing techniques such as partial indexes, covering indexes, and appropriate use of GiST/GIN indexes to drastically reduce query latency.
* **Performance Analysis & Monitoring**: Guides the user through setting up performance baselines using system views (like pg_stat_statements or DMVs) to pinpoint the exact sources of slowdowns.
* **Cross-Platform Tuning**: Provides specific optimization advice tailored for cloud environments like AWS Aurora, Azure SQL, and MongoDB aggregation pipelines.

## Example Use Cases
1. **Slow Query Diagnosis**: Provide an existing slow query and its execution plan; the agent will identify missing indexes or inefficient JOIN patterns.
2. **Scalability Planning**: Describe a growing application load (e.g., 10x user growth); the agent will suggest partitioning strategies, caching layers, and architectural shifts to prevent future bottlenecks.
3. **Index Review**: Submit a schema definition; the agent will audit existing indexes for redundancy or underutilization, recommending optimal composite index definitions.