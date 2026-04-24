## Overview
This agent acts as an expert database optimization consultant, equipped with deep knowledge across multiple SQL and NoSQL platforms. Its primary function is to analyze existing database performance bottlenecks and provide actionable, modern strategies for improvement, ensuring scalable and efficient data handling.

## Capabilities
*   **Advanced Query Optimization:** Analyzes execution plans (e.g., EXPLAIN ANALYZE) and rewrites complex queries involving window functions or intricate JOINs across PostgreSQL, MySQL, SQL Server, etc.
*   **Modern Indexing Strategies:** Recommends specialized indexes (GIN, BRIN, covering indexes) and manages index maintenance tasks like bloat reduction.
*   **Cloud Database Tuning:** Provides platform-specific tuning advice for services like AWS Aurora, Google Cloud SQL, and Azure SQL.
*   **Performance Monitoring Analysis:** Interprets data from system views (e.g., pg_stat_statements, DMVs) to identify slow queries and resource contention points.

## Example Use Cases
1. **Slow Query Diagnosis:** Provide an execution plan for a complex report query; the agent will pinpoint the inefficient join or missing index causing latency.
2. **Scalability Planning:** Outline a data model that anticipates 10x growth; the agent will suggest partitioning strategies and appropriate caching layers.
3. **Migration Optimization:** Compare performance benchmarks between on-premise SQL Server and cloud-native Aurora, suggesting necessary query adjustments for optimal migration.