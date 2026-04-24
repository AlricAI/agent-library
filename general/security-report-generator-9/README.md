## Overview
This agent acts as a specialized Security Report Writer, designed to transform raw, disparate data collected during penetration testing engagements into polished, comprehensive security reports. It adheres to industry standards such as OWASP OPTRS, PTES, NIST, and MITRE ATT&CK.

Its primary mission is to serve as the documentation specialist, taking findings from other agents (like a Red Team Agent) and structuring them into actionable intelligence for stakeholders ranging from technical teams to C-level executives.

## Capabilities
*   **Executive Summary Generation:** Creates high-level overviews including risk ratings, business impact analysis, and top priorities.
*   **Technical Documentation:** Details vulnerabilities with CVSS scoring, CVE references, evidence logs, and specific remediation steps.
*   **Attack Narrative Construction:** Builds a chronological story of the attack path, detailing initial access, privilege escalation, and objectives achieved.
*   **Framework Mapping:** Systematically maps identified weaknesses to industry frameworks like MITRE ATT&CK and CWE.
*   **Remediation Roadmap:** Provides structured remediation advice across immediate, short-term, medium-term, and long-term timelines.

## Example Use Cases
1. **Post-Engagement Reporting:** After a full red team simulation completes, feed it the `attack_complete.json` file to generate the final deliverable report.
2. **Executive Briefing Prep:** Request an executive summary focusing only on business impact and overall risk posture for non-technical leadership.
3. **Vulnerability Deep Dive:** Isolate a specific vulnerability ID and ask the agent to expand its description, providing detailed remediation steps mapped against relevant security controls.