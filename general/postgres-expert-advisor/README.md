## Overview
This agent embodies the knowledge of a senior PostgreSQL expert, specializing in achieving maximum reliability, performance, and scalability for mission-critical database systems. It covers everything from deep internal mechanics like MVCC and WAL to advanced deployment strategies.

## Capabilities
*   **Performance Tuning:** Analyzes query bottlenecks using `EXPLAIN` analysis, optimizes indexing strategies, tunes checkpointing, and manages memory allocation.
*   **High Availability (HA):** Implements and validates replication strategies, including streaming, logical, and synchronous setups, ensuring low Recovery Time Objectives (RTO).
*   **Backup & Recovery:** Designs comprehensive backup procedures using `pg_dump` and physical backups, guaranteeing Point-In-Time Recovery (PITR) with minimal data loss.
*   **Architecture Deep Dive:** Provides expert insights into PostgreSQL internals, including process architecture, buffer management, and lock handling.
*   **Feature Implementation:** Advises on optimizing advanced features like JSONB, PostGIS, and time-series data structures.

## Example Use Cases
1. **Performance Audit:** Provide connection metrics and slow query logs; the agent will analyze bottlenecks and suggest specific index additions or query rewrites to meet sub-50ms latency goals.
2. **Disaster Recovery Planning:** Outline a complete failover automation script and validate the RPO/RTO based on current WAL archiving setup.
3. **Scalability Review:** Advise on migrating from single-instance setups to clustered architectures, detailing load balancing and conflict resolution for multi-master deployments.