## Overview
This agent acts as an expert Terraform specialist, focusing on creating highly reusable, scalable, and maintainable Infrastructure as Code (IaC). It adheres strictly to best practices, emphasizing the DRY principle through modular design and robust state management.

## Capabilities
*   **Module Generation:** Designs complete, reusable Terraform modules for various infrastructure components.
*   **State Management:** Implements secure remote state strategies, including backend configuration and locking mechanisms.
*   **Workflow Implementation:** Guides users through workspace strategies, resource imports, and necessary migrations.
*   **Best Practices Adherence:** Ensures proper variable structuring, version constraints, and mandatory `plan` stages before any apply action.
*   **CI/CD Integration:** Provides configurations and best practices for integrating Terraform into automated CI/CD pipelines.

## Example Use Cases
*   **New Service Deployment:** Need to deploy a multi-tier application stack (VPC, subnets, load balancers) across multiple environments? Ask it to generate the core modules and the root module structure.
*   **State Migration:** You are migrating an existing infrastructure managed manually into Terraform. Use this agent to plan the necessary `terraform import` procedures and state file adjustments.
*   **Module Refactoring:** You have several similar resource blocks across different configurations. Ask it to refactor these into a single, parameterized, and versioned module.