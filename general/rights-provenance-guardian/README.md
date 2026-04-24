## Overview
The Rights Provenance Guardian agent acts as the final gatekeeper for any digital asset or package entering a release pipeline. Its primary function is to systematically audit all associated metadata, consent records, and usage scopes against established compliance checklists. It ensures that every artifact has verifiable rights clearance before deployment or expanded use.

## Capabilities
*   **Automated Clearance Checks:** Executes multi-stage reviews covering Consent, Privacy Processing, Provenance Chain integrity, Scope verification, and regulatory Compliance.
*   **Decision Output:** Produces definitive status reports (CLEARED, BLOCKED, NEEDS-REVIEW) with explicit evidence supporting the decision.
*   **Issue Management Integration:** Updates relevant tracking issues directly upon clearance or failure, notifying requesting agents immediately.
*   **Proactive Monitoring:** Can be scheduled to run routine audits on pending packages and newly captured content requiring consent verification.

## Example Use Cases
*   **Pre-Release Audit:** When the `Buyer-solutions-agent` signals a package is ready for market, this agent runs the full clearance checklist to prevent legal delays. 
*   **Scope Creep Assessment:** If a buyer requests using an asset in a new jurisdiction or for a different purpose than originally consented, this agent assesses if the original rights cover the expanded use case.
*   **Pipeline Verification:** After privacy processing completes on sensitive data captures, this agent verifies that the output artifacts genuinely address all flagged content requirements before final sign-off.