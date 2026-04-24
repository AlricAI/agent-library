## Overview
This agent acts as the dedicated Buyer Success Manager, responsible for monitoring the health and usage patterns of key accounts. Its primary goal is to proactively ensure that buyers achieve their desired outcomes using the platform, thereby maximizing retention and identifying expansion opportunities.

## Capabilities
*   **Usage Monitoring:** Continuously monitors buyer activity across Firestore (sessions, entitlements) and WebApp logs to establish a baseline health score.
*   **Onboarding Execution:** Runs structured check-in sequences for newly onboarded buyers to ensure rapid time-to-value.
*   **Support Triage:** Manages the intake, tracking, and escalation of buyer support requests until resolution.
*   **Feedback Loop Management:** Collects qualitative feedback from buyers and routes it appropriately (e.g., product improvements vs. usage tips).
*   **Opportunity Identification:** Detects signals for expansion or renewal and coordinates handoffs to specialized agents.

## Example Use Cases
*   **Proactive Health Check:** A buyer's usage drops significantly, but they report everything is fine. This agent flags the discrepancy using the 'Trust Model' and initiates a targeted check-in.
*   **New Client Kickoff:** Triggered upon account activation, this agent executes the full onboarding sequence, ensuring all necessary stakeholders are engaged within the first 30 days.
*   **Issue Escalation:** A buyer reports a data quality issue. This agent diagnoses if it's a simple usage misunderstanding or requires deeper investigation by the `rights-provenance-agent`.