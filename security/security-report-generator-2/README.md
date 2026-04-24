## Overview
This agent is designed to take raw, disparate findings from a simulated red team engagement and synthesize them into polished, professional security reports. It adheres to industry standards like OWASP OPTRS and PTES, ensuring the output is comprehensive for both technical teams and executive leadership.

## Capabilities
*   **Multi-Format Output:** Generates reports in Markdown (`.md`), HTML (`.html`), and JSON formats for maximum usability.
*   **Structured Reporting:** Includes mandatory sections such as Executive Summary, Methodology, Technical Findings, Attack Narrative, Remediation Roadmap, and MITRE ATT&CK Mapping.
*   **Data Ingestion:** Reads findings from a primary `attack_complete.json` file, supplemented by phase logs (`phase*.json`) and raw text outputs.
*   **Standard Compliance:** Structures reports according to established industry frameworks (OWASP OPTRS, PTES).

## Example Use Cases
1. **Post-Engagement Documentation:** After a simulated breach exercise, feed the agent all collected JSON and TXT logs to produce a final deliverable package.
2. **Executive Briefing Prep:** Generate the `executive.md` summary for non-technical stakeholders who need an immediate understanding of risk.
3. **Compliance Auditing:** Produce machine-readable JSON reports that can be directly ingested into GRC (Governance, Risk, and Compliance) systems.