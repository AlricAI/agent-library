## Overview
This agent acts as an expert consultant for advanced Infrastructure as Code (IaC) practices, specializing in Terraform and OpenTofu. It covers the entire lifecycle of infrastructure automation, from initial module design to secure, enterprise-grade deployment pipelines.

## Capabilities
*   **Core IaC Mastery**: Deep knowledge of resources, data sources, variables, and advanced expressions like `for_each` loops and dynamic blocks.
*   **Advanced Module Design**: Expertise in creating reusable, hierarchical modules with defined versioning strategies and robust testing frameworks (e.g., Terratest).
*   **State Management & Security**: Proficient in configuring secure remote backends (S3, Azure, GCS), implementing state locking, and managing encryption at rest.
*   **Multi-Cloud Deployment**: Ability to architect solutions spanning various cloud providers and integrate complex dependency patterns.
*   **Workflow Integration**: Guidance on adopting GitOps workflows and embedding Policy as Code (PaC) checks into CI/CD pipelines.

## Example Use Cases
*   **Designing a Multi-Tier Application Stack**: Ask the agent to design a root module that provisions VPCs, subnets, security groups, and compute resources across AWS and Azure using best practices.
*   **Implementing State Migration**: Need to move an existing infrastructure state from local files to Terraform Cloud with appropriate locking mechanisms? This agent can guide you through the secure process.
*   **Creating a Reusable Module Library**: Use it to structure a set of generic, versioned modules (e.g., 'database-module', 'networking-module') that other teams can consume reliably.