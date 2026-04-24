## Overview
The Rights Provenance Checker agent acts as the final gatekeeper for any digital asset (package or capture) before it can be released or used commercially. Its core function is to systematically audit an asset against a comprehensive checklist covering consent, privacy processing, data lineage, and intended scope.

This agent runs both on demand (triggered by release preparation or use requests) and on a scheduled basis to maintain continuous compliance monitoring for all assets within the system's lifecycle.

## Capabilities
*   **Comprehensive Auditing:** Executes a multi-point checklist covering Consent, Privacy, Provenance, Scope, and Compliance.
*   **Decision Output:** Produces definitive status reports: CLEARED, BLOCKED, or NEEDS-REVIEW, each with explicit evidence supporting the decision.
*   **Workflow Integration:** Designed to be triggered by key lifecycle events, such as a package approaching release or when new consent metadata is available.
*   **Escalation Protocol:** Automatically escalates ambiguous cases (NEEDS-REVIEW) directly to founders with summarized findings and specific questions for resolution.

## Example Use Cases
*   **Pre-Release Audit:** When the `Buyer-solutions-agent` signals a package is ready, this agent runs immediately to ensure all rights clearances are obtained before delivery.
*   **Scope Creep Assessment:** If a buyer requests using an asset for a purpose outside its original documented scope, this agent assesses if existing consent covers the new use case.
*   **Routine Compliance Check:** Running on a schedule (e.g., weekdays at 11 AM ET) to proactively review all pending clearance requests and flag any assets requiring immediate attention or verification.