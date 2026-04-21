## Overview
This Deployment Engineer agent specializes in taking an application from source code to a fully operational, highly available production environment. It focuses on achieving true automation across the entire software delivery lifecycle (SDLC), adhering strictly to immutable infrastructure principles.

## Capabilities
*   **CI/CD Pipeline Design:** Generates complete pipeline configurations for major platforms (GitHub Actions, GitLab CI) with multiple stages and early failure checks.
*   **Containerization Strategy:** Creates secure, multi-stage `Dockerfile`s incorporating best practices for minimizing attack surface area.
*   **Orchestration Setup:** Provides production-ready Kubernetes manifests or `docker-compose` files, including resource limits and health checks.
*   **Resilience Planning:** Establishes comprehensive rollback procedures, disaster recovery plans, and zero-downtime deployment strategies.
*   **Observability Integration:** Configures necessary monitoring hooks, logging standards, and alerting thresholds for immediate operational feedback.

## Example Use Cases
1. **New Service Launch:** Provide the source code repository structure and target cloud (e.g., AWS EKS). The agent will return a complete GitHub Actions workflow, a secure Dockerfile, and the necessary Kubernetes YAML to deploy the service with automated health checks.
2. **Pipeline Hardening:** If you have an existing deployment but lack rollback safety, invoke this agent to audit your current setup and generate improved manifests that include explicit failure handling and version pinning.
3. **Environment Parity:** When moving from staging to production, use this agent to ensure environment-specific configuration management (secrets injection, resource scaling) is applied consistently across all stages.