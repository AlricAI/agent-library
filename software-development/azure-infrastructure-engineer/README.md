## Overview
This agent acts as a senior Azure Infrastructure Specialist, focusing on designing, automating, and securing end-to-end cloud architectures within the Microsoft Azure ecosystem. It ensures that all deployments adhere to industry best practices, emphasizing infrastructure-as-code (IaC) principles for repeatability and governance.

## Capabilities
*   **Azure Resource Architecture:** Designs foundational elements including resource group strategies, tagging standards, Virtual Machine setup, Storage accounts, Network Security Groups (NSG), and implements governance via Azure Policies and Management Groups.
*   **Hybrid Identity & Entra ID Integration:** Manages secure identity patterns, covering synchronization architectures (AAD Connect/Cloud Sync), Conditional Access policies, and the proper use of Managed Identities and Service Principals.
*   **Automation & IaC Mastery:** Generates robust automation using PowerShell with the Az module, models infrastructure using Bicep or ARM templates, and integrates deployments into CI/CD pipelines (GitHub Actions).
*   **Operational Excellence:** Provides guidance on monitoring setup, cost optimization strategies, and implementing safe deployment patterns with documented rollback procedures.

## Example Use Cases
1.  **Network Deployment:** "Generate the Bicep template required to deploy a multi-VNet structure across three distinct Azure regions, including necessary routing rules." 
2.  **Automation Flow:** "Write a PowerShell script using Az modules that provisions and configures a set of VMs in a specific resource group while enforcing least-privilege RBAC."
3.  **Identity Hardening:** "Outline the steps and required policies to enforce MFA via Conditional Access for all administrative roles accessing Azure resources."
4.  **Compliance Audit:** "Develop a checklist or script logic to audit existing subscriptions for non-compliant tagging or overly permissive NSG rules."

This agent is ideal when you need to move beyond simple resource creation and require architecturally sound, automated, and governable cloud deployments.