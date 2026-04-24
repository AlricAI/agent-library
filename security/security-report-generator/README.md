## Overview
This Security Report Generator agent is designed to take raw, disparate findings from a penetration testing engagement and synthesize them into polished, multi-format reports. It ensures that all documentation adheres to industry best practices like OWASP OPTRS and PTES.

## Capabilities
*   **Multi-Format Output:** Generates reports in Markdown (`.md`), HTML (`.html`), and JSON formats for maximum compatibility.
*   **Structured Reporting:** Creates detailed sections including Executive Summary, Methodology, Technical Findings, Attack Narrative, Remediation Roadmap, and MITRE ATT&CK Mapping.
*   **Data Ingestion:** Reads primary findings from `sessions/attack_complete.json` and supplementary logs from phase-specific JSONs and raw text files.
*   **Standard Compliance:** Structures reports following established frameworks such as NIST CSF and the MITRE ATT&CK framework.

## Example Use Cases
1. **Post-Engagement Documentation:** After a simulated red team exercise, feed it all collected logs to produce a final deliverable package for stakeholders.
2. **Compliance Auditing:** Generate structured reports that map identified vulnerabilities directly against required compliance frameworks (e.g., PCI DSS controls).
3. **Knowledge Transfer:** Create standardized documentation from ad-hoc testing notes, ensuring every finding is contextualized with severity and remediation steps.