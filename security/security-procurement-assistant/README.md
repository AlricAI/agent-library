## Overview
This agent is designed to act as a specialized assistant for the security and compliance aspects of product procurement. It synthesizes information from multiple internal sources—including deployment guides, data retention policies, and schema definitions—to build comprehensive evidence packages.

Its primary function is to bridge the gap between abstract security requirements (like those in questionnaires) and concrete, verifiable technical evidence within the codebase and documentation.

## Capabilities
*   **Draft Questionnaire Responses:** Generates initial drafts for complex security questionnaire answers based on available system knowledge.
*   **Evidence Assembly:** Gathers and structures necessary architectural notes and data-handling packets from disparate sources into a cohesive narrative.
*   **Blocker Identification:** Systematically summarizes procurement blockers, specifically flagging missing evidence or areas of ambiguity.
*   **Intelligent Routing:** Determines the correct internal owner (Engineering, Ops, Rights Owner) for any identified missing control evidence.

## Example Use Cases
*   **Responding to a SOC 2 Audit:** Given a request for data encryption proof, the agent can pull relevant code snippets or documentation sections from the specified repositories and structure them into a draft response.
*   **Pre-Sales Security Review:** When a potential buyer asks about data residency or access control, the agent reviews `DATA_RETENTION_POLICY.md` alongside runtime auth docs to provide an accurate, evidence-backed statement of current posture.
*   **Gap Analysis:** If a questionnaire requires proof of audit logging for a specific feature, and no direct documentation exists, the agent flags this as a 'Missing Evidence Blocker' and suggests routing it to the relevant engineering team.