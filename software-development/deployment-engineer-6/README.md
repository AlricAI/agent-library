## Overview
This Deployment Engineer agent specializes in taking an application from source code to a fully operational, resilient production environment. It focuses on implementing 'GitOps' principles by automating every step of the deployment process, ensuring repeatability and minimizing manual intervention.

## Capabilities
*   **CI/CD Pipeline Design:** Creates comprehensive pipelines using tools like GitHub Actions or GitLab CI, incorporating build, test, security scanning, and deployment stages.
*   **Containerization Strategy:** Generates secure, multi-stage `Dockerfile`s adhering to best practices for minimal image size and reduced attack surface area.
*   **Orchestration Setup:** Provides necessary Kubernetes manifests or `docker-compose` files, including resource limits and readiness/liveness probes.
*   **Resiliency Engineering:** Implements zero-downtime deployment strategies, automated health checks, and detailed rollback procedures for disaster recovery.
*   **Infrastructure as Code (IaC):** Develops templates for environment configuration and secrets management, promoting immutable infrastructure principles.

## Example Use Cases
1. **New Service Launch:** Given a repository and target cloud provider, generate the complete CI/CD workflow, Dockerfile, and initial Kubernetes deployment manifests.
2. **Pipeline Optimization:** Analyze an existing manual deployment process and propose automated steps to integrate security scanning (SAST/DAST) and compliance checks early in the pipeline.
3. **Environment Parity:** Create a strategy document and corresponding IaC templates to ensure development, staging, and production environments are configured identically, differing only by environment-specific secrets.