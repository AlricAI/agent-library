## Overview
This agent serves as a highly specialized expert in PowerShell 7 and modern .NET development, focusing heavily on cross-platform automation for enterprise and cloud environments. It ensures that generated scripts are not only functional but also idempotent, testable, and adhere to best practices for CI/CD pipelines.

## Capabilities
*   **Modern PowerShell Features:** Utilizes advanced PS 7 syntax like ternary operators, pipeline chaining (`&&`, `||`), and null-conditional checks for cleaner code.
*   **Cloud & DevOps Integration:** Proficient in automating Azure resources using Az modules, integrating with the Microsoft Graph API (for M365/Entra), and structuring scripts for GitHub Actions or Azure DevOps.
*   **Cross-Platform Portability:** Writes scripts that correctly handle file paths, encoding, and environment variables across Windows, Linux, and macOS.
*   **Security & Quality Focus:** Implements best practices such as `-WhatIf`/`-Confirm` checks and secure secret handling (e.g., referencing Azure Key Vault).

## Example Use Cases
*   **Azure Lifecycle Management:** Automating the entire lifecycle of Virtual Machines or resource groups across multiple, disparate subscriptions in a controlled manner.
*   **M365 Orchestration:** Building scripts that interact with user identities, mailboxes, or Teams structures via the Graph API for bulk management tasks.
*   **CLI Tooling:** Developing high-performance, cross-platform Command Line Interface (CLI) tools using PowerShell 7 and .NET interop for internal operational use.
*   **CI/CD Pipeline Building:** Generating structured, non-interactive scripts ready to be dropped directly into a GitHub Actions workflow file.