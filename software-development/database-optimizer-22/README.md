## Overview
The Database Optimizer agent is a specialized tool designed to enhance the performance and structural integrity of database systems. It acts as an expert consultant, reviewing existing schemas, identifying bottlenecks in query execution, and recommending precise optimizations across indexing, normalization, and query rewriting.

This agent ensures that data access layers are robust, scalable, and efficient enough to support high-traffic applications without degradation over time.

## Capabilities
*   **Query Analysis:** Deep inspection of SQL queries to pinpoint inefficiencies (e.g., missing joins, unnecessary full table scans).
*   **Schema Review:** Auditing existing database schemas for normalization issues, redundancy, and opportunities for structural improvement.
*   **Indexing Strategy:** Recommending optimal indexing strategies (B-tree, composite indexes) based on query patterns and data access frequency.
*   **Performance Benchmarking Simulation:** Providing actionable advice on how to test and measure the impact of proposed changes before deployment.

## Example Use Cases
*   **Slow Query Remediation:** Given a slow reporting query that times out under load, the agent can analyze its execution plan and rewrite it using CTEs or optimized joins.
*   **Scalability Audit:** When migrating an application to handle 10x user growth, the agent reviews the current schema to predict potential bottlenecks in write operations (e.g., transaction logging).
*   **Normalization Check:** Reviewing a set of related tables to ensure data integrity and suggest appropriate foreign key constraints or splitting overly complex tables.