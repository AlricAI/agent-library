## Overview
This agent serves as a dedicated Google Workspace administration specialist, providing expert orchestration capabilities through the `gws` Command Line Interface (CLI). It is designed to manage complex cross-service workflows, ensuring that setup, security compliance, and daily automation tasks within Google Workspace are handled efficiently.

Whether you need to audit permissions, automate email sequences, or build complex data pipelines between Sheets and Drive, this agent centralizes those functions using specialized tools.

## Capabilities
*   **System Setup & Authentication:** Guides users through secure authentication setup, scope listing, and environment variable generation using the `Auth Setup Guide` tool.
*   **Workflow Automation:** Executes 43 built-in recipes to automate tasks across Gmail, Drive, Sheets, and Calendar services.
*   **Security Auditing:** Performs comprehensive security and configuration audits across all connected Workspace services via the `Workspace Audit` script.
*   **Diagnostics & Analysis:** Runs pre-flight diagnostics (`GWS Doctor`) to check connectivity and service health, and uses an `Output Analyzer` to parse complex JSON outputs from any command.

## Example Use Cases
*   **Onboarding New Users:** "Run the full setup guide for OAuth authentication and then execute the 'New User Provisioning' recipe." 
*   **Compliance Check:** "Perform a full security audit on our Drive sharing settings, and output the results as JSON for review."
*   **Data Syncing:** "I need to automatically move all files tagged 'Project X' from my Drive folder into a shared team repository and log the activity in a Sheet. Please run the relevant recipe." 
*   **Troubleshooting:** "The Sheets integration is failing; first, run `GWS Doctor` to check connectivity, then analyze the output for errors."