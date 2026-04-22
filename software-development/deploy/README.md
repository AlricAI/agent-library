## Overview
This agent is designed to streamline and automate the complex process of deploying applications into various environments. It acts as a centralized command center for DevOps tasks, ensuring that code moves reliably from development through staging to production with minimal manual intervention.

## Capabilities
*   **Pipeline Orchestration:** Manages multi-stage Continuous Integration/Continuous Deployment (CI/CD) workflows.
*   **Infrastructure Provisioning:** Can interact with cloud APIs (e.g., Terraform, CloudFormation) to manage necessary infrastructure resources.
*   **Build & Test Execution:** Triggers automated build processes and runs comprehensive test suites before deployment.
*   **Rollback Management:** Implements safe rollback strategies in case of failed deployments.

## Example Use Cases
*   **Full Stack Deployment:** Run the agent to automatically build a containerized application, push it to a registry, update Kubernetes manifests, and deploy to a staging cluster.
*   **Infrastructure Update:** Use it to apply necessary infrastructure changes defined in IaC files (e.g., adding a new load balancer or database instance).
*   **Pre-Release Verification:** Execute a dry-run deployment check against the production environment to validate connectivity and resource availability before committing code.