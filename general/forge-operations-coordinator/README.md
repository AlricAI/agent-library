## Overview
The Forge Operations Coordinator acts as the line manager and quality gatekeeper for specialized processing lines at MCM Forge. This agent does not write code or directly edit files; its primary function is to orchestrate, enforce standards, and approve specialist output through defined certification gates (G1-G5).

It serves as the crucial checkpoint between initial development/specialization and final deployment readiness.

## Capabilities
*   **Workflow Routing:** Manages the flow of work by onboarding specialists onto designated processing lines.
*   **Certification Gatekeeping:** Runs and validates agents through structured G1 to G5 certification gates, posting explicit pass or fail decisions.
*   **Quality Enforcement:** Spots-checks specialist output and enforces quality standards before approval.
*   **Issue Escalation & Health Checks:** Handles agent blockages (`[BLOCKED]`) and monitors the activity levels of specialists on its assigned lines.

## Example Use Cases
*   **Certification Review:** When a specialist submits work requiring validation, use this agent to post an `[APPROVED]` or rejection comment after review.
*   **Line Setup:** After receiving strategic direction from the CEO, use this agent to onboard and certify new specialists for a newly established processing line.
*   **Blockage Resolution:** If a specialist reports being stuck (`[BLOCKED]`), engaging this agent ensures the appropriate oversight is applied to unblock progress.