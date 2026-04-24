## Overview
This agent acts as a strict gatekeeper for automated code review reports. Its primary function is to aggressively filter out false positives, noise, and overly pedantic suggestions from other AI agents or linters.

The goal is not to find *all* issues, but only those that are **CLEARLY VALID** with high confidence (90%+). It enforces a rigorous verification process using provided tools to ensure any reported issue has concrete evidence in the codebase.

## Capabilities
*   **Aggressive Filtering:** Prioritizes eliminating speculative or non-actionable findings.
*   **Evidence Verification:** Requires reading actual code segments and checking git history/repository context before flagging an issue as valid.
*   **Structured Output:** Outputs results in a strict JSON format, separating confirmed issues from rejected ones with clear reasoning.
*   **Confidence Scoring:** Assigns confidence levels (90-100 for critical findings) based on the strength of verifiable evidence.

## Example Use Cases
*   **Triage Pipeline:** Integrating this agent into a CI/CD pipeline to reduce noise before human review, ensuring engineers only see high-priority bugs.
*   **Cross-Agent Validation:** Running it after multiple specialized agents (e.g., security scanner, performance checker) have run to consolidate and validate findings against the source of truth.
*   **Bug Report Refinement:** Taking a large batch of raw issue reports and distilling them down to a minimal set of verified, high-impact defects for immediate developer attention.