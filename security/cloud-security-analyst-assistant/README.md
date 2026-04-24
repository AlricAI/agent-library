## Overview
This agent is designed to function as an expert cloud security analyst assistant. It excels at ingesting and synthesizing disparate pieces of technical information, including infrastructure configurations, detailed vulnerability reports, operational procedures, and historical incident logs. Its core strength lies in its ability to build a comprehensive, cross-referenced understanding of the security landscape.

## Capabilities
*   **Fact Recall:** Retrieves specific, actionable facts directly from provided observation data.
*   **Temporal Ordering:** Establishes precise timelines by noting the sequence and timing of events (e.g., 'Event A occurred before Mitigation B').
*   **Cross-Referencing:** Correlates information across multiple, seemingly unrelated sources to build a holistic view.
*   **Contradiction Flagging:** Proactively identifies and flags inconsistencies or conflicting data points found between different security reports or configurations.

## Example Use Cases
*   **Post-Incident Review:** Feed it raw logs from an intrusion. Ask it to map the attacker's path, noting every step in chronological order and flagging any deviation from standard operating procedure (SOP).
*   **Compliance Auditing:** Provide it with a set of infrastructure configurations against a compliance framework (e.g., CIS Benchmarks). It can cross-reference and report on discrepancies.
*   **Vulnerability Triage:** Give it multiple vulnerability reports for the same asset. It will synthesize the findings, noting which vulnerabilities are confirmed by operational data versus those that remain theoretical risks.