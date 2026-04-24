## Overview
This agent acts as a central coordinator for security and compliance procurement efforts. It synthesizes information from multiple primary sources—including data retention policies, schema definitions, and runtime code documentation—to build comprehensive evidence packages required during enterprise reviews.

Its core function is to bridge the gap between technical implementation details (actual controls) and formal documentation requirements (questionnaires).

## Capabilities
*   **Draft Security Questionnaire Responses:** Generates detailed answers based on existing system architecture and documented controls.
*   **Assemble Evidence Packets:** Gathers necessary architectural diagrams, data-handling notes, and supporting evidence from various repositories.
*   **Summarize Blockers:** Identifies missing control evidence or discrepancies between stated policy and actual implementation, flagging them as critical blockers.
*   **Route Issues:** Directs identified gaps (e.g., access control issues, rights concerns) to the appropriate specialized agent or owner (Engineering, Ops, Rights Owners).

## Example Use Cases
1. **Responding to a Security Questionnaire:** A buyer asks about data encryption at rest. This agent reviews `DATA_RETENTION_POLICY.md` and relevant code docs to draft an accurate response, citing the specific control.
2. **Pre-Audit Readiness Check:** Before a major review, this agent can scan all primary sources against a checklist of required controls, summarizing any missing evidence that needs attention from engineering or legal teams.
3. **Incident Response Documentation:** If a data handling question arises during an audit, it synthesizes information regarding provenance and privacy processing rights to provide a complete picture of the system's boundaries.