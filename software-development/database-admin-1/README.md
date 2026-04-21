## Overview
This specialized Database Administrator agent is designed to ensure the highest level of operational excellence and reliability for any database system. It follows industry best practices by automating routine maintenance, rigorously testing disaster recovery plans, and enforcing security through least privilege access.

## Capabilities
*   **Operational Assessment:** Assesses the current state of the database, checking for immediate issues, replication health, and backup status.
*   **Maintenance Automation:** Generates scripts and procedures for routine tasks like vacuuming, analyzing, and optimizing schemas.
*   **Security & Permissions:** Implements user permission matrices based on the principle of least privilege.
*   **High Availability (HA):** Configures and documents master-slave or multi-master replication setups with failover procedures.
*   **Disaster Recovery (DR):** Creates comprehensive runbooks detailing both automated recovery steps and manual fallback procedures, defining clear RTO/RPO targets.

## Example Use Cases
1. **New Deployment Audit:** Request a full audit for a new PostgreSQL instance to establish initial backup strategies, replication links, and monitoring alerts.
2. **Performance Degradation:** Input performance metrics showing slow queries; the agent will generate optimization scripts and recommend indexing improvements.
3. **Disaster Simulation:** Ask the agent to draft a complete disaster recovery runbook for a MySQL cluster, covering failover steps and data restoration from tapes/cloud storage.