## Overview
Database Optimizer Pro is an expert AI agent designed to tackle the most complex database performance challenges. It possesses deep, modern knowledge across multiple SQL and NoSQL platforms, specializing in transforming slow, inefficient databases into high-throughput, scalable systems.

This agent goes beyond simple query fixes; it analyzes execution plans, recommends advanced indexing strategies (like BRIN or partial indexes), and advises on cloud-native optimization techniques for services like Aurora or Cloud SQL.

## Capabilities
*   **Advanced Query Optimization**: Analyzes `EXPLAIN ANALYZE` output, rewrites complex queries involving window functions, and optimizes JOINs across various databases (PostgreSQL, MySQL, etc.).
*   **Modern Indexing Strategies**: Recommends optimal index types (B-tree, GIN, GiST) and structures composite indexes to maximize read/write efficiency.
*   **Performance Monitoring & Analysis**: Interprets metrics from system views (e.g., `pg_stat_statements`, DMVs) to pinpoint bottlenecks, detect blocking queries, and establish performance baselines.
*   **Cloud Database Tuning**: Provides specific tuning advice for major cloud providers' database offerings.
*   **NoSQL Optimization**: Assists with optimizing complex aggregation pipelines in MongoDB or designing efficient access patterns for DynamoDB.

## Example Use Cases
1. **Slow Report Generation**: Provide an inefficient SQL query and the associated execution plan; the agent will rewrite it, suggest necessary indexes, and explain the performance gain.
2. **Scaling Assessment**: Describe a growing application load (e.g., 10x traffic increase); the agent will recommend architectural changes, such as read replicas, partitioning schemes, or caching layers.
3. **Index Selection**: Present a schema with high write volume on specific columns; the agent will advise whether a covering index, partial index, or different data type might be more appropriate than a standard B-tree.