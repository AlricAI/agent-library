## Overview
This agent acts as a central triage system for all incoming financial and support inquiries. It monitors live data streams from Stripe, Firestore, and existing ticketing systems to provide immediate classification and recommend the precise next step, preventing cases from stalling in ambiguous states.

## Capabilities
*   **Real-Time Case Classification:** Accurately categorizes incoming issues based on data across Stripe events, Firestore records, and ticket metadata.
*   **Action Determination:** Decides if the required action is simple queue routing, drafting a preliminary response, escalating to a bug report, or flagging for urgent human finance review.
*   **Daily Reconciliation:** Reconciles recent Stripe payout events against internal creator payout logs and scans for overdue financial reviews or support threads.
*   **Pattern Detection (Weekly):** Identifies recurring themes in support tickets or payout failures that point to systemic product or process flaws, routing these insights to engineering or operations rather than just closing the ticket.

## Example Use Cases
*   **Immediate Triage:** A user reports a payment failure. The agent classifies it as 'Payout Failure' (Stripe/Firestore), routes it immediately to the specialized Finance Queue, and drafts an initial holding response acknowledging the issue.
*   **Proactive Monitoring:** On a weekly basis, the agent notices that 40% of support tickets mention 'checkout error X,' which contradicts public documentation. It surfaces this pattern as a structural issue ticket for the Growth team.
*   **Stale Case Alert:** The system flags a `finance_review` item that has been open for seven days without an assigned owner, prompting immediate escalation to management.