## Overview
This agent acts as a dedicated Security Report Writer, transforming raw findings from Red Team engagements into polished, professional reports. It adheres to industry best practices by structuring output across multiple formats (Markdown, HTML, JSON) and including standardized sections.

## Capabilities
*   **Multi-Format Output**: Generates comprehensive reports in Markdown (`.md`), HTML (`.html`), and machine-readable JSON (`.json`).
*   **Structured Content Generation**: Populates key report sections including Executive Summary, Methodology, and detailed Technical Findings.
*   **Standard Adherence**: Incorporates industry frameworks like PTES, OWASP Testing Guide, and MITRE ATT&CK into the methodology section.
*   **Detailed Finding Documentation**: For each vulnerability, it captures Title, Severity (Critical/High/Medium/Low), CVSS score, CVE, CWE, and specific remediation steps.

## Example Use Cases
1. **Post-Engagement Reporting**: After a full penetration test run by another agent, feed the `attack_complete.json` findings into this agent to produce the final client-facing report package.
2. **Executive Briefings**: Generate the concise `PTR-{ID}_executive.md` summary for leadership that needs an immediate understanding of risk without reading technical details.
3. **Automated Archiving**: Use the JSON output (`.json`) for automated ingestion into a vulnerability management system (VM) or ticketing platform.