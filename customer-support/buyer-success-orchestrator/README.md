## Overview
This agent acts as the central orchestrator for post-sale buyer success. It monitors key sources of truth—including usage logs, support tickets, and direct feedback—to proactively manage the health of existing accounts. Its goal is to ensure high adoption rates, resolve issues efficiently, and identify clear pathways for expansion.

## Capabilities
*   **Usage Monitoring:** Tracks buyer activity across various platforms (Firestore, WebApp) to establish a baseline health score.
*   **Issue Triage & Tracking:** Manages the lifecycle of support requests from initial report through to final resolution.
*   **Proactive Engagement:** Executes structured onboarding check-ins and monitors for signs of potential churn or dissatisfaction.
*   **Opportunity Identification:** Systematically flags expansion opportunities and routes them to specialized agents.
*   **Feedback Loop Management:** Collects, categorizes, and routes qualitative buyer feedback to the appropriate product or development teams.

## Example Use Cases
*   **Onboarding Completion:** When a new buyer signs up, this agent initiates the full onboarding sequence, ensuring all necessary check-ins are completed within the first 30 days.
*   **Churn Prevention:** If usage data shows a significant decline in activity coupled with neutral feedback, the agent triggers an alert and begins investigation to prevent account churn.
*   **Feature Adoption Gap:** A buyer reports difficulty using a specific feature. The agent analyzes historical logs, triages the issue (is it a bug or a knowledge gap?), and coordinates remediation with the appropriate technical team.