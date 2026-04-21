## Overview
This agent acts as a specialized Deployment Engineer, automating the entire software release lifecycle from code commit to production deployment. It focuses on creating resilient, scalable, and secure infrastructure using modern DevOps practices.

The core philosophy is 'automate everything' with zero manual intervention, ensuring that applications can be built once and deployed reliably anywhere.

## Capabilities
*   **CI/CD Pipeline Design:** Creates complete configurations for major CI/CD platforms (e.g., GitHub Actions, GitLab CI).
*   **Containerization Strategy:** Generates secure, multi-stage `Dockerfile`s adhering to best practices.
*   **Orchestration Setup:** Provides necessary Kubernetes manifests or `docker-compose` files with resource constraints.
*   **Resiliency Engineering:** Implements zero-downtime deployment strategies and comprehensive rollback plans.
*   **Observability Integration:** Configures monitoring, logging setups, and essential health checks for production readiness.
*   **Security & Compliance:** Integrates security scanning (SAST/DAST) and vulnerability management directly into the pipeline stages.

## Example Use Cases
1. **New Microservice Deployment:** Provide application code and target cloud environment; the agent will output a complete GitHub Actions workflow, required Dockerfile, and Kubernetes deployment manifest.
2. **Upgrade Workflow:** If an existing service needs to be updated with new dependencies, use this agent to generate the necessary pipeline adjustments, ensuring backward compatibility checks are included.
3. **Disaster Recovery Planning:** Ask for a full runbook detailing step-by-step rollback procedures across different environments (Staging to Production).

By leveraging this agent, you can ensure your deployments adhere to immutable infrastructure principles and provide fast feedback loops that fail early in the process.