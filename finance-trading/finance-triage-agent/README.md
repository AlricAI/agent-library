## Overview
The Finance Triage Agent is designed to act as a central intelligence layer for all incoming financial and customer support interactions. It moves beyond simple ticket routing by analyzing the context across multiple data sources—including live Stripe events, Firestore records, and existing ticket states—to determine the precise nature of the issue.

Its core function is to triage urgency and complexity, ensuring that every trigger results in a clear, actionable next step for either an automated agent or a human specialist.

## Capabilities
*   **Real-Time Classification:** Accurately classifies incoming cases by cross-referencing data from Stripe, Firestore, and ticket metadata.
*   **Action Determination:** Decides the optimal workflow path: queue routing, response drafting, bug escalation, or immediate urgent human finance review.
*   **Daily Reconciliation:** Automatically reconciles recent Stripe payment events against internal payout records (`creatorPayouts`).
*   **Proactive Monitoring:** Scans for overdue items in financial reviews and stagnant support threads to prevent aging issues.
*   **Pattern Detection (Weekly):** Identifies recurring themes, systemic failure patterns (e.g., specific payout failures), or product confusion that require engineering or operations intervention rather than just isolated support replies.

## Example Use Cases
*   **Handling a Payout Failure:** When Stripe reports a failed payout, the agent doesn't just flag it; it checks the associated workflow in Firestore, determines if manual owner assignment is needed, and drafts an escalation ticket for the finance team.
*   **Identifying Product Friction:** If the agent detects three support tickets within a week all mentioning confusion about a specific product feature's billing cycle, it flags this as a 'Structural Issue' requiring documentation updates or product changes, rather than just answering individual questions.
*   **Intelligent Routing:** Upon receiving a ticket flagged with both a payment ID and keywords like 'dispute,' the agent routes it directly to the specialized Disputes Queue while simultaneously drafting an initial holding response for the customer.