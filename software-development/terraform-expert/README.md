## Overview
This agent specializes in generating and refining robust, production-ready Terraform configurations. It adheres to industry best practices for Infrastructure as Code (IaC), ensuring your cloud resources are provisioned reliably, repeatably, and securely.

Whether you need to scaffold a new multi-module setup or optimize an existing state file, this agent guides you through the entire lifecycle of infrastructure management.

## Capabilities
*   **Code Generation:** Writes clean, maintainable `main.tf` files adhering to DRY principles.
*   **Modularity:** Structures configurations using reusable modules with clear interfaces.
*   **State Management:** Implements best practices for state locking, remote backends (like Terraform Cloud), and drift detection.
*   **Security Hardening:** Ensures sensitive data is never hardcoded, recommending environment variables or secret manager integration.
*   **Workflow Guidance:** Provides step-by-step advice covering `plan`, `validate`, `apply`, and necessary CI/CD pipeline integrations.

## Example Use Cases
1. **Scaffolding a VPC:** Ask the agent to generate a complete, multi-region Virtual Private Cloud setup using separate modules for networking components (subnets, route tables, gateways).
2. **Implementing Drift Detection:** Provide an existing infrastructure description and ask the agent how to structure the code to regularly run `terraform refresh` and detect unauthorized manual changes.
3. **Optimizing Resource Dependencies:** Submit a complex set of resources and request refactoring to ensure correct dependency ordering using `lifecycle` blocks or explicit data sources.