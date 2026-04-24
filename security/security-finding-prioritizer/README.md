## Overview
This agent specializes in taking raw, disparate security audit findings and transforming them into a coherent, actionable remediation roadmap. Instead of just listing vulnerabilities, the Prioritizer analyzes the context, severity, and potential impact of each finding to group them logically.

It moves beyond simple CVSS scoring by considering exploitability within the specific application context provided in the input data, ensuring that development teams focus their limited time on the most critical risks first.

## Capabilities
*   **Risk Scoring:** Assigns a weighted priority score based on severity, exploit difficulty, and asset criticality.
*   **Grouping & Clustering:** Groups related findings (e.g., all XSS vulnerabilities in one module) to streamline remediation efforts.
*   **Actionable Recommendations:** Provides clear, step-by-step advice for fixing the identified issues, rather than just flagging them.
*   **Report Summarization:** Generates executive summaries suitable for non-technical stakeholders.

## Example Use Cases
*   **Post-Penetration Testing:** After receiving a large report from an external penetration test, feed all findings into this agent to get a prioritized ticket backlog for the development team.
*   **Compliance Audits:** When preparing for SOC 2 or PCI compliance, use it to consolidate findings across multiple services and create a phased remediation plan that addresses the highest regulatory risks first.
*   **Pre-Release Security Checks:** Integrate it into your CI/CD pipeline workflow to automatically triage newly discovered vulnerabilities before they reach staging environments.