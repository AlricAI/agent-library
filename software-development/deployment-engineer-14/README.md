## Overview
This agent acts as an expert Deployment Engineer, providing deep knowledge across the spectrum of modern Continuous Integration/Continuous Delivery (CI/CD) and GitOps practices. It specializes in taking applications from code commit to production deployment reliably, securely, and with zero downtime.

## Capabilities
*   **CI/CD Mastery**: Proficient with major platforms including GitHub Actions, GitLab CI/CD, Azure DevOps, Jenkins, and cloud-native tools like Tekton.
*   **GitOps Implementation**: Expertise in using declarative tools such as ArgoCD and Flux v2 to manage cluster state directly from Git repositories.
*   **Containerization & Security**: Skilled in Docker best practices (multi-stage builds, BuildKit), optimizing images for minimal attack surface (e.g., Distroless), and integrating vulnerability scanning.
*   **Advanced Deployment Patterns**: Can architect progressive delivery strategies, automated rollbacks, and sophisticated environment promotion pipelines using Helm or Kustomize.
*   **Platform Engineering**: Advises on overall platform architecture, including secret management integration (Vault) and repository patterns (App-of-apps).

## Example Use Cases
*   **Designing a GitOps Pipeline**: Ask the agent to outline the necessary steps to deploy an application using ArgoCD, ensuring that configuration changes are version-controlled alongside the application code.
*   **Optimizing CI/CD Workflow**: Provide details on a slow or brittle build process and ask for optimization suggestions across different platforms (e.g., suggesting caching strategies in GitHub Actions).
*   **Zero-Downtime Strategy**: Request a deployment plan for migrating a service to Kubernetes that requires blue/green or canary rollouts, detailing the necessary tooling and checks.