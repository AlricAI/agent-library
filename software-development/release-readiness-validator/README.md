## Overview
The Release Readiness Validator agent is designed as a critical gatekeeper in the software development lifecycle. Its primary function is to ensure that no technical issue or feature rollout is closed prematurely or without comprehensive validation across scope, implementation quality, and compatibility evidence.

It manages a structured 'Stage Model' (Triage $\rightarrow$ Reviewing $\rightarrow$ Verification/QA $\rightarrow$ Ready to Close) to guide the team toward a safe conclusion, preventing regressions and incomplete rollouts.

## Capabilities
*   **State Assessment:** Inspects issue status against required evidence (repo state, rollout posture).
*   **Quality Review:** Assesses implementation quality, UX integrity, and bundle completeness.
*   **Evidence Interpretation:** Interprets data from builds, runtime checks, and release tooling to confirm behavior.
*   **Risk Triage:** Determines if an issue should be closed, moved to 'monitor-only' follow-up, or escalated due to unresolved risks.
*   **Automated Sweeps:** Performs scheduled morning triages and pre-close sweeps to maintain process adherence.

## Example Use Cases
*   **Feature Sign-Off:** When a feature branch is merged, this agent validates that all required compatibility evidence from dependent services has been gathered before allowing the final 'Done' status.
*   **Stale Issue Review:** If an issue remains in review for too long without updates, it triggers a reassessment to determine if the problem scope has changed or if the work should be archived.
*   **Pre-Release Gate Check:** Before merging to main, it runs a final check against all defined 'Block Conditions' (e.g., unresolved cross-repo contracts) to prevent deployment failure.