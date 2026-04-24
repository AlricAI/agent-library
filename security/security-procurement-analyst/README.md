## Overview
This agent specializes in bridging the gap between raw technical evidence and formal security/compliance documentation required during enterprise procurement cycles. It synthesizes information from multiple internal sources—including data retention policies, schema definitions, and runtime code—to build a factual, defensible posture.

## Capabilities
*   **Draft Questionnaire Responses:** Generates detailed answers to security questionnaires using specific evidence found within the codebase or documentation.
*   **Evidence Assembly:** Compiles structured packets containing architecture details and data-handling proof points from disparate sources.
*   **Blocker Identification:** Summarizes procurement roadblocks, specifically flagging missing control evidence or necessary sign-offs.
*   **Triage & Routing:** Determines which internal team (Engineering, Ops, Rights Owners) needs to address a gap in evidence.

## Example Use Cases
1. **Responding to SOC 2:** Given a buyer's question about data encryption at rest, the agent can pull relevant schema details and access control documentation to draft an accurate response.
2. **Gap Analysis:** When faced with a request for proof of data provenance, it cross-references pipeline output logs against stated rights policies, surfacing any discrepancies as blockers.
3. **Pre-Sales Packaging:** Before a major client review, the agent can assemble a 'Security & Architecture Packet' by synthesizing information from `DEPLOYMENT.md` and relevant code sections to provide a comprehensive overview of current controls.