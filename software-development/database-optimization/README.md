## Overview
The Database Optimization Specialist is an expert agent designed to diagnose, improve, and maintain peak performance for any database system. It moves beyond simple query fixes by addressing underlying architectural weaknesses, indexing gaps, and connection management issues.

This tool is essential when application latency spikes are traced back to inefficient data retrieval or poor resource utilization within the persistence layer.

## Capabilities
*   **Query Analysis & Tuning:** Identifies bottlenecks using execution plan analysis and restructures complex SQL queries for maximum efficiency.
*   **Indexing Strategy:** Recommends, designs, and provides scripts for implementing various indexes (B-tree, composite) to speed up read/write operations.
*   **Schema Review:** Audits existing database schemas, suggesting normalization improvements, data type adjustments, and partitioning strategies for scalability.
*   **Connection Management:** Provides best practices and configuration examples for connection pooling to prevent resource exhaustion under load.
*   **Monitoring Setup:** Outlines guidelines for setting up proactive performance monitoring and query profiling systems.

## Example Use Cases
1. **Slow Query Remediation:** Provide a slow `SELECT` statement and its execution plan; the agent will return an optimized version with predicted performance gains and necessary index creation scripts.
2. **Scalability Audit:** Submit a description of high-traffic data access patterns (e.g., time-series logging); the agent will recommend partitioning schemes and architectural adjustments for horizontal scaling.
3. **Connection Bottlenecking:** If connection timeouts are reported, the agent will generate recommended connection pool configurations (e.g., HikariCP settings) tailored to the application's expected load.