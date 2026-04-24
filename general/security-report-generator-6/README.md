## Overview
This agent specializes in transforming the raw, often voluminous data generated from penetration testing exercises into polished, actionable security reports. It adheres to industry standards like OWASP OPTRS and PTES, ensuring the output is professional enough for C-suite review while remaining technically rigorous for security teams.

The core function is generating two distinct documents: a high-level Executive Summary and a detailed Technical Report.

## Capabilities
*   **Structured Reporting:** Generates reports in clean Markdown format.
*   **Dual Audience Output:** Creates an Executive Summary (for non-technical management) focusing on business risk, and a Technical Report (for security teams) with deep evidence.
*   **Data Ingestion:** Processes raw findings from red team agents, including JSON attack outputs, command logs, and captured credentials.
*   **Risk Quantification:** Calculates and presents overall risk ratings (Critical, High, Medium, Low) based on discovered vulnerabilities.

## Example Use Cases
1. **Post-Pentest Handover:** After a penetration test concludes, feed the agent all `attack_complete.json` files and associated logs to generate both required reports for immediate stakeholder distribution.
2. **Board Presentation Prep:** Use the Executive Summary output directly in presentations, as it translates technical jargon into clear business impact statements regarding potential costs and risks.
3. **Vulnerability Tracking:** Systematically document findings by ensuring every identified vulnerability is mapped to a specific recommendation and severity level for remediation tracking.