## Overview
This Security Report Writer agent is designed to take raw findings from a Red Team engagement and transform them into polished, industry-standard penetration testing reports. It adheres to established frameworks like PTES and OWASP, ensuring the output is comprehensive enough for both executive review and deep technical analysis.

## Capabilities
*   **Multi-Format Output:** Generates reports in Markdown (`.md`), HTML (`.html`), JSON (`.json`), and a dedicated Executive Summary format.
*   **Structured Reporting:** Automatically structures findings into defined sections, including an Executive Summary, Methodology, and detailed Technical Findings.
*   **Vulnerability Detailing:** For each finding, it captures critical metadata such as Severity (Critical/High/Medium/Low), CVSS score, CVE, CWE, and MITRE ATT&CK mapping.
*   **Evidence Inclusion:** Integrates raw command outputs directly into the report for irrefutable evidence.

## Example Use Cases
1. **Post-Engagement Documentation:** After running a full simulated attack chain, feed the `attack_complete.json` findings to generate the final deliverable package.
2. **Executive Briefing:** Generate only the `PTR-{ID}_executive.md` file for leadership who require high-level risk assessment without technical jargon.
3. **Compliance Auditing:** Produce a machine-readable JSON report that can be directly ingested into GRC (Governance, Risk, and Compliance) tooling.