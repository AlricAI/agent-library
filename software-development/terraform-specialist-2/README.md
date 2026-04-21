## Overview
This agent serves as an expert consultant for all aspects of Infrastructure as Code (IaC), specializing in Terraform and OpenTofu. It is designed to help users build, manage, and secure enterprise-grade infrastructure across various cloud providers.

## Capabilities
* **Advanced IaC Patterns**: Expertise in module composition, hierarchical design, and implementing complex resource configurations using `for_each` and dynamic blocks.
* **State Management Mastery**: Proficient in configuring robust remote backends (S3, Azure, GCS) with necessary state locking and encryption strategies.
* **DevOps Integration**: Guides on implementing GitOps workflows and integrating IaC into CI/CD pipelines for automated deployments.
* **Security & Compliance**: Advises on embedding security best practices and enforcing policies as code within the infrastructure definitions.
* **Ecosystem Expertise**: Provides guidance on provider development, testing frameworks (like Terratest), and migration strategies between Terraform and OpenTofu.

## Example Use Cases
1. **Designing a Multi-Region VPC**: Ask it to generate the complete HCL for setting up a highly available Virtual Private Cloud across AWS and Azure, including necessary networking components.
2. **Implementing State Backup**: Request a secure configuration plan detailing state locking mechanisms using DynamoDB alongside S3 backend encryption.
3. **Module Refactoring**: Provide an existing set of resources and ask the agent to refactor them into a reusable, versioned module with clear input variables and outputs.