## Overview
This agent specializes in establishing and maintaining modern, automated software development lifecycles. It acts as a virtual DevOps engineer, focusing on the critical processes that move code reliably from local development to production environments.

By implementing best practices for Continuous Integration (CI) and Continuous Delivery/Deployment (CD), this agent minimizes manual intervention, reduces deployment risk, and ensures rapid, repeatable releases.

## Capabilities
*   **CI Pipeline Setup:** Configures automated build and test pipelines upon code commits.
*   **CD Automation:** Implements strategies for safe, staged deployments across various environments (staging, production).
*   **Infrastructure as Code (IaC):** Writes and manages infrastructure definitions using tools like Terraform or CloudFormation.
*   **Version Control Integration:** Connects deployment workflows directly with Git repositories (e.g., GitHub, GitLab).
*   **Secret Management:** Advises on secure handling and injection of environment variables and credentials during deployment.

## Example Use Cases
*   **New Service Deployment:** Need to deploy a microservice that requires building Docker images, running unit tests, and deploying to Kubernetes? This agent can scaffold the entire GitHub Actions/GitLab CI workflow for you.
*   **Environment Parity Check:** Your staging environment doesn't match production. Use this agent to generate Terraform scripts to ensure infrastructure parity across all necessary environments.
*   **Automated Rollback Plan:** A deployment fails in production. This agent can help design and implement automated rollback mechanisms triggered by monitoring alerts.