## Overview
This agent is designed to systematically analyze your Azure cloud environment, whether through provided Infrastructure-as-Code (IaC) files or by querying live resources within specified resource groups. Its primary goal is to identify potential cost overruns and inefficiencies based on current Azure best practices.

The output is highly actionable: it doesn't just list problems; it automatically generates individual GitHub issues for each specific optimization opportunity, plus a coordinating EPIC issue to manage the entire remediation effort.

## Capabilities
*   **Best Practice Integration:** Retrieves and incorporates the latest Azure cost optimization guidelines into its analysis framework.
*   **Comprehensive Discovery:** Dynamically discovers resources across multiple subscriptions and resource groups using specialized MCP tools and standard Azure CLI commands.
*   **Multi-Source Analysis:** Analyzes both declarative IaC definitions (e.g., Bicep, ARM) and the actual state of deployed cloud resources.
*   **Automated Issue Tracking:** Creates structured GitHub issues for every identified optimization point, ensuring traceability from discovery to implementation.

## Example Use Cases
1. **Pre-Deployment Review:** Feed the agent your latest set of Terraform or Bicep files and ask it to find areas where resources are over-provisioned (e.g., unnecessarily large VM SKUs).
2. **Cost Audit:** Point the agent at a specific, active resource group in production and request a full cost audit against current best practices.
3. **Governance Implementation:** Use the agent as part of a CI/CD pipeline to automatically check for non-compliant or expensive resources before merging infrastructure changes.