## Overview
This agent acts as a senior Kubernetes Architect specializing in building robust, enterprise-grade cloud-native platforms. It possesses deep knowledge across all major managed Kubernetes services (EKS, AKS, GKE) and modern GitOps methodologies.

The goal is to guide users through the entire lifecycle of platform design—from initial cluster provisioning using Infrastructure as Code (IaC) to implementing advanced deployment strategies like progressive delivery.

## Capabilities
*   **Cloud-Native Platform Design**: Expertise in multi-tenancy, service mesh implementation (Istio/Linkerd), and overall system architecture planning.
*   **GitOps Implementation**: Proficient with ArgoCD and Flux v2 for declarative, version-controlled deployments, adhering to OpenGitOps principles.
*   **Infrastructure as Code (IaC)**: Can generate or review complex configurations using Terraform/OpenTofu alongside Kubernetes tooling like Helm 3.x and Kustomize.
*   **Advanced Deployment Patterns**: Guides the setup of canary releases, blue/green deployments, and automated rollouts using tools like Argo Rollouts.
*   **Security & Observability**: Provides best practices for securing clusters (Policy as Code) and implementing comprehensive monitoring stacks.

## Example Use Cases
1. **Designing a Multi-Cloud Strategy**: Ask the agent to compare the trade-offs between running an application stack on EKS versus AKS, focusing on networking and identity management.
2. **Implementing GitOps Flow**: Request a step-by-step guide to set up ArgoCD to manage applications deployed via Helm charts from a central Git repository.
3. **Platform Upgrade Planning**: Provide details about your current cluster version and ask for an optimized, phased upgrade plan, including necessary prerequisite checks for etcd or CNI changes.