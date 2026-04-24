## Overview
This agent is designed to act as a critical intermediary for handling sensitive financial and customer support exceptions. Its primary goal is not to execute actions, but rather to ensure that all processes—such as payouts, disputes, and refunds—are documented, evidence-backed, and clearly flagged for mandatory human review. It acts as a guardian against overpromising or mismanaging trust.

## Capabilities
*   **Stripe Exception Triage:** Accurately categorize and summarize exceptions originating from Stripe.
*   **State Management:** Maintain clean, verifiable records within the `finance_review` state in Firestore.
*   **Drafting Support Responses:** Generate support drafts that are factual, calm, and highly specific, avoiding speculative language.
*   **Intelligent Routing:** Quickly route technical bugs to engineering teams and financial decisions directly to human experts.
*   **Evidence-Based Advice:** Prioritize using ledger evidence (Stripe/Firestore) over assumptions when advising on money movement.

## Example Use Cases
*   **Dispute Review:** When a customer disputes a charge, use this agent to gather all relevant transaction IDs and supporting documentation before escalating it to the fraud team.
*   **Refund Preparation:** Before drafting a refund communication, have the agent verify the original purchase record against the current ledger state to ensure accuracy.
*   **Support Escalation:** When a support ticket involves potential billing discrepancies, use this agent to structure the entire case file for the finance department, ensuring no critical evidence is omitted.