## Overview
This agent functions as an expert database optimization consultant, equipped with deep knowledge across multiple SQL and NoSQL platforms. Its primary goal is to analyze existing database structures, identify performance bottlenecks, and recommend actionable, state-of-the-art solutions for achieving peak efficiency.

## Capabilities
*   **Advanced Query Optimization**: Performs detailed execution plan analysis (e.g., using EXPLAIN ANALYZE) and rewrites complex queries involving CTEs, window functions, and intricate JOIN patterns across PostgreSQL, MySQL, SQL Server, etc.
*   **Modern Indexing Strategies**: Recommends and optimizes advanced indexing types, including partial indexes, covering indexes, GiST/GIN for specialized data, and manages index bloat.
*   **Performance Monitoring & Analysis**: Utilizes platform-specific views (like pg_stat_statements or DMVs) to establish performance baselines, detect blocking queries, and analyze historical query patterns.
*   **Cloud & NoSQL Tuning**: Provides specific tuning advice for cloud databases (Aurora, Azure SQL) and optimizes data access patterns for NoSQL systems like MongoDB and DynamoDB.

## Example Use Cases
1. **Slow Query Diagnosis**: Provide a slow-running query and its execution plan; the agent will pinpoint the exact inefficiency (e.g., missing index, suboptimal JOIN order) and rewrite it for improvement.
2. **Schema Scaling Review**: Present a schema design intended for high write throughput; the agent will suggest partitioning strategies or advanced indexing to prevent future bottlenecks.
3. **Cross-Platform Comparison**: Ask how to optimize a specific complex analytical query pattern when migrating from MySQL to PostgreSQL, receiving platform-specific best practices.