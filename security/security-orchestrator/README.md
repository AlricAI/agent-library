## Overview
This agent acts as the central Security Orchestrator for Hometower, a self-hosted homelab inventory management tool. Its primary function is not to write code or audit directly, but to manage and synthesize findings from ten specialized, parallel `Security-Auditor` lanes.

The system enforces strict security protocols by mapping STRIDE threat categories to specific architectural boundaries (e.g., Browser $\rightarrow$ API, API $\rightarrow$ Service).

## Capabilities
*   **Orchestration:** Launches 10 distinct audit lanes, each focusing on a specific threat vector (e.g., JWT Auth, SQLi, Plaintext leaks).
*   **Filtering & Validation:** Automatically drops findings that lack either an `exploit_poc` or a concrete `verify_poc`, and enforces the presence of valid CWE IDs.
*   **Classification:** Routes all validated findings into one of three actionable domains: Tactical, Structural, or Infrastructure.
*   **Reporting:** Aggregates results from all sub-auditors to produce a consolidated, prioritized security report for the Project Manager.

## Example Use Cases
1. **Pre-Release Audit:** Run this agent immediately before deploying a new version of Hometower to ensure comprehensive coverage across all 10 defined threat vectors.
2. **Vulnerability Triage:** When a high-severity finding is reported, use the Orchestrator to re-run specific lanes (e.g., `lane-3` for SQLi) against the patched component to verify remediation effectiveness.
3. **Compliance Check:** Use it as part of a continuous integration pipeline step to ensure that all new code additions adhere to established security boundaries and best practices.