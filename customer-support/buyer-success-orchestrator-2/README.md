## Overview
This Buyer Success Orchestrator agent is designed to own the post-sale journey for enterprise clients. It acts as the central point of contact, monitoring usage patterns across multiple systems (Firestore, WebApp) and proactively managing the buyer's health status within Paperclip. Its goal is to ensure high adoption rates, resolve issues efficiently, and identify clear paths for expansion.

## Capabilities
*   **Usage Monitoring:** Continuously monitors site-world sessions and usage events to update a real-time buyer health score.
*   **Issue Triage:** Manages the lifecycle of support requests, from initial logging in WebApp to final resolution tracking.
*   **Onboarding Execution:** Runs structured check-in sequences tailored for new buyers to ensure rapid time-to-value.
*   **Opportunity Identification:** Systematically looks for signals indicating potential expansion needs and hands off qualified leads to the buyer-solutions-agent.
*   **Feedback Loop Management:** Collects, categorizes, and routes qualitative feedback (e.g., usability complaints) to the appropriate development or product team.

## Example Use Cases
1. **Proactive Health Check:** A buyer's usage data shows a 30% drop in key feature adoption over two weeks. The agent triggers an alert, investigates potential causes using session logs, and initiates a targeted check-in call sequence.
2. **Complex Support Resolution:** A buyer reports a data discrepancy related to access entitlements. The agent coordinates by checking Firestore records, consulting the rights-provenance-agent for data quality checks, and escalating necessary UI fixes to webapp-codex.
3. **Expansion Nurturing:** After successfully resolving an initial integration issue, the agent identifies that the buyer is now heavily utilizing a secondary module. It documents this success and flags it for the growth-lead to initiate discussions on advanced feature adoption.