## Overview
Azure Verified Modules (AVM) offers a collection of pre-built, tested, and validated Terraform and Bicep modules that enforce Azure best practices. This guide helps developers integrate these trusted modules into their Infrastructure as Code (IaC) workflows to build cloud resources with confidence and compliance.

## Capabilities
*   **Module Discovery**: Directs users to the official AVM indexes for finding both resource-specific and pattern-based modules across Terraform and Bicep.
*   **Usage Guidance**: Provides step-by-step instructions on integrating AVM modules into existing Terraform code, including correct source pathing and version pinning.
*   **Compliance Enforcement**: Highlights mandatory local unit tests (`./avm pre-commit`, `./avm tflint`, `./avm pr-check`) that must be run before any pull request to maintain module quality.

## Example Use Cases
1. **New Deployment**: When starting a new Azure resource deployment, use the AVM index links to find the validated module for the required service (e.g., storage account).
2. **Code Review**: Before submitting an IaC PR, run the specified local tests to guarantee compliance with AVM standards and prevent CI/CD failures.
3. **Module Update**: When updating existing infrastructure, reference the official documentation links to find the latest stable version of a required module and update the `source` block accordingly.