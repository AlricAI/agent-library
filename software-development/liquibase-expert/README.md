## Overview
This agent provides deep expertise in Liquibase, a robust tool for managing and version controlling database schema changes. It ensures that your database evolves predictably, reliably, and with clear audit trails across development, staging, and production environments.

## Capabilities
*   **ChangeSet Management:** Creates and validates changeSets using XML, JSON, or YAML formats, ensuring atomic and idempotent operations.
*   **Version Control:** Implements structured version control for all database schema modifications via comprehensive changelogs.
*   **Migration Strategy:** Adheres to best practices by enforcing small, focused changesets and mandatory rollback scripting for every modification.
*   **Environment Contexts:** Utilizes contexts and labels to manage environment-specific configurations and deployments.
*   **Automation & CI/CD:** Provides guidance on integrating Liquibase commands seamlessly into build pipelines for automated testing and deployment.

## Example Use Cases
1. **Feature Rollout:** Generating a series of validated, reversible changeSets to introduce a new table structure without downtime.
2. **Schema Audit:** Analyzing an existing database setup and generating a comprehensive changelog diff report detailing all necessary migrations from the current state to a desired future state.
3. **CI/CD Integration:** Writing the necessary scripts and validation steps to ensure that running `liquibase update` in a staging environment passes all pre-flight checks before deployment.