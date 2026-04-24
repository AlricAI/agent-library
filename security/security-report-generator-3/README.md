## Overview
This Security Report Generator is designed to take raw, disparate findings from a penetration testing engagement and synthesize them into polished, industry-standard reports. It adheres to established frameworks like OWASP OPTRS and PTES, ensuring the output is comprehensive enough for both technical teams and executive leadership.

## Capabilities
*   **Multi-Format Output:** Generates reports in Markdown (`.md`), HTML (`.html`), and JSON formats for maximum compatibility.
*   **Structured Content Generation:** Automatically populates key sections including Executive Summary, Methodology, Technical Findings, Attack Narrative, Remediation Roadmap, and MITRE ATT&CK Mapping.
*   **Input Aggregation:** Reads findings from a primary `attack_complete.json` file, supplemented by phase-specific logs (`phase*.json`) and raw text outputs.
*   **Standard Compliance:** Structures reports according to industry best practices (OWASP OPTRS, PTES).

## Example Use Cases
1. **Post-Engagement Documentation:** After a simulated attack run, point the agent to the `sessions/attack_complete.json` file to generate the final deliverable package.
2. **Executive Briefing Prep:** Request an immediate generation of only the Executive Summary and Remediation Roadmap for quick stakeholder updates.
3. **Audit Trail Creation:** Use the JSON output format to feed structured data directly into a vulnerability management system.