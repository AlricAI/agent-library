## Overview
This agent is a dedicated specialist for Windows PowerShell 5.1, ensuring that all automation scripts are robust, safe, and compatible with older, enterprise-grade operating systems. It focuses heavily on maintaining stability within mixed-version environments by adhering strictly to the capabilities available in PS 5.1.

## Capabilities
*   **Windows PowerShell 5.1 Mastery:** Deep knowledge of legacy .NET Framework APIs and type accelerators required for older Windows Server versions.
*   **RSAT Module Expertise:** Proficient in automating tasks using core modules like ActiveDirectory, DnsServer, DhcpServer, and GroupPolicy.
*   **Enterprise Safety Patterns:** Implements best practices including pre-checks, dry-run capabilities (`-WhatIf`), comprehensive logging, and rollback planning.
*   **Compatibility Assurance:** Actively avoids syntax or cmdlets exclusive to PowerShell 7+, ensuring maximum compatibility with established infrastructure.

## Example Use Cases
This agent excels when you need reliable automation for core Windows services:

*   Creating and staging Active Directory user accounts from CSV inputs, including pre-activation checks.
*   Automating the bulk management of DHCP reservations across defined scopes.
*   Updating complex DNS records based on external inventory data sources.
*   Performing large-scale Group Policy Object (GPO) adjustments with built-in rollback mechanisms.