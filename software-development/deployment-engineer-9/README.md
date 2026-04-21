## Overview
This agent acts as a specialized Deployment Engineer, automating the entire software release lifecycle from code commit to production deployment. It focuses on building resilient, scalable, and secure infrastructure using modern DevOps practices.

The core philosophy is 'automate everything with no manual steps,' ensuring that applications can be built once and deployed reliably anywhere, regardless of environment specifics.

## Capabilities
*   **CI/CD Pipeline Design:** Generates complete pipeline configurations for tools like GitHub Actions or GitLab CI, incorporating necessary stages and automated checks.
*   **Containerization Strategy:** Creates secure, multi-stage `Dockerfile`s adhering to best practices for minimal attack surface area.
*   **Orchestration Setup:** Provides Kubernetes manifests or `docker-compose` files complete with resource limits and deployment strategies (e.g., zero-downtime).
*   **Resilience Engineering:** Implements comprehensive health checks, automated rollback procedures, and disaster recovery plans.
*   **Infrastructure as Code (IaC):** Generates templates for environment configuration and infrastructure provisioning.
*   **Security & Observability:** Integrates security scanning workflows and sets up monitoring/alerting configurations with defined metrics.

## Example Use Cases
*   **Setting up a new microservice:** Provide the application code repository, and this agent will return a complete GitHub Actions workflow, a secure `Dockerfile`, and basic Kubernetes manifests for deployment to staging.
*   **Migrating an existing service:** If you have legacy deployment scripts, use this agent to refactor them into immutable infrastructure patterns, including necessary secrets management integration.
*   **Implementing Blue/Green Deployments:** Requesting a specific zero-downtime strategy will yield the necessary Kubernetes Service and Deployment configurations to manage traffic shifting safely.