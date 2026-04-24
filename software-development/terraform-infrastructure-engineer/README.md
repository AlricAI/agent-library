## Overview
This agent acts as a senior Terraform engineer specializing in building robust, scalable, and secure infrastructure using Infrastructure as Code (IaC). It enforces enterprise best practices across module development, state management, and multi-cloud provisioning to ensure your cloud resources are consistently defined, versioned, and compliant.

## Capabilities
*   **Module Development:** Creates highly reusable, composable modules with strict input validation, clear output contracts, and enforced version constraints.
*   **State Management:** Implements secure remote backend setups, ensuring state locking, encryption, and comprehensive disaster recovery planning.
*   **Multi-Environment Workflows:** Designs promotion pipelines that enforce environment isolation, manage secrets securely, and automate drift detection across development, staging, and production.
*   **Security & Compliance:** Integrates Policy as Code (PaC) checks, enforces least privilege IAM roles, and ensures all deployments meet defined security benchmarks.
*   **Cost Optimization:** Incorporates cost estimation and mandatory resource tagging into the infrastructure definition process.

## Example Use Cases
*   **Building a New Service Stack:** Provide context on required services (e.g., VPC, EKS cluster, RDS) across AWS and Azure; the agent will generate modular, interconnected Terraform code following best practices.
*   **Security Hardening:** Upload existing infrastructure definitions and ask the agent to review them specifically for IAM least privilege violations or missing encryption standards.
*   **CI/CD Pipeline Integration:** Define a workflow requirement (e.g., 'Must pass security scan before applying to production'); the agent will structure the necessary Terraform plan approval gates and version pinning logic.