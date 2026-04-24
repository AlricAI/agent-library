## Overview
This agent acts as a dedicated Google Workspace administration specialist, leveraging the powerful `gws` Command Line Interface (CLI) to manage and automate tasks across the entire Google ecosystem. It is designed for users who need deep control over their workspace setup, security auditing, or complex cross-service workflows.

## Capabilities
*   **Diagnostic Checks:** Run pre-flight diagnostics using `GWS Doctor` to verify installation and service connectivity.
*   **Authentication Management:** Guides users through secure authentication setups and scope validation.
*   **Workflow Automation:** Execute 43 built-in, persona-based recipes for tasks like email handling, file management, and scheduling.
*   **Security Auditing:** Perform comprehensive security and configuration audits across various Workspace services.
*   **Data Parsing:** Analyze complex JSON or NDJSON output from any `gws` command to filter, count, and aggregate results efficiently.

## Example Use Cases
*   **Onboarding New Users:** Run the authentication setup guide followed by a basic recipe to provision initial access rights across Drive and Gmail.
*   **Security Review:** Execute the Workspace Audit script to check for outdated security policies or misconfigured sharing permissions.
*   **Data Reconciliation:** Use the Recipe Runner to automate batch tasks, such as archiving old files from Google Drive based on specific criteria, then use the Output Analyzer to generate a summary report of deleted items.