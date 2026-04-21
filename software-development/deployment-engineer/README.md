## Overview
This agent acts as a senior Deployment Engineer, providing expertise across the entire software delivery lifecycle. It specializes in implementing modern Continuous Integration/Continuous Delivery (CI/CD) practices, adopting GitOps methodologies, and ensuring robust, scalable deployments for containerized applications on Kubernetes.

The goal is to move beyond simple scripting by architecting resilient pipelines that prioritize security, reliability, and developer experience.

## Capabilities
*   **Advanced CI/CD Platform Mastery**: Proficient in configuring workflows across GitHub Actions, GitLab CI/CD, Azure DevOps, and Jenkins, including reusable actions and pipeline optimization.
*   **GitOps Implementation**: Expertise with tools like ArgoCD and Flux v2 for declarative infrastructure management, handling app-of-apps patterns and environment promotion.
*   **Container Security & Build Optimization**: Skilled in Docker best practices (multi-stage builds, minimal base images), vulnerability scanning integration, and using secure runtimes like Podman or Distroless.
*   **Progressive Delivery**: Ability to design rollouts incorporating canary deployments and automated rollback strategies for zero-downtime updates.
*   **Configuration Management**: Generates solutions using Helm, Kustomize, and integrates external secret management systems (e.g., Vault).

## Example Use Cases
1. **Designing a GitOps Pipeline**: Ask the agent to outline the necessary steps to deploy an application from a GitHub push into a staging environment using ArgoCD, detailing required manifests for Flux/Argo.
2. **Optimizing Build Security**: Provide a basic Dockerfile and ask the agent to refactor it to minimize the attack surface by implementing non-root users and multi-stage builds.
3. **Comparing CI Tools**: Request a comparison between setting up environment approvals in GitHub Actions versus Azure DevOps for a regulated deployment process.