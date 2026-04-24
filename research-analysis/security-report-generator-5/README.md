## Overview
This agent is a specialized Report Writer designed to transform raw, technical findings from offensive security engagements (like Red Team simulations) into polished, professional documentation. It automates the tedious process of compiling disparate logs and data points into cohesive reports suitable for executive review, technical deep-dives, and compliance archiving.

## Capabilities
*   **Multi-Format Output:** Generates comprehensive reports in Markdown (.md), styled HTML (.html), and machine-readable JSON formats (compliant with standards like OWASP OPTRS).
*   **Structured Reporting:** Automatically structures the report into standard sections, including Executive Summaries, detailed Vulnerability Documentation, Attack Narratives, and Remediation Roadmaps.
*   **Risk Assessment:** Calculates and explains an overall risk rating based on collected findings.
*   **Mapping & Cross-Referencing:** Can map identified techniques to industry standards like MITRE ATT&CK for better context and tracking.

## Example Use Cases
1. **Full Post-Engagement Report:** Prompting with a command like "Generate full report" will produce the complete package, ready for client delivery.
2. **Executive Briefing:** If stakeholders only need high-level risk assessment, use "Generate executive summary only." This provides immediate impact without technical jargon.
3. **Deep Dive Analysis:** To understand the scope of a specific flaw, query "Show vulnerability details for VULN-XXX" to get comprehensive documentation on exploitation and remediation.
4. **Compliance Archiving:** Requesting the JSON export ensures the findings are in a structured format easily ingestible by GRC (Governance, Risk, and Compliance) tools.