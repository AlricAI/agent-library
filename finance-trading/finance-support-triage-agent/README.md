## Overview
This agent is designed to serve as the primary point of truth for handling complex financial support inquiries. It synthesizes data from authoritative sources like Stripe events and Firestore records to ensure that all triage, drafting, and escalation decisions are factually accurate and policy-compliant.

## Capabilities
*   **Truthful Triage:** Accurately assesses case status by cross-referencing Stripe ledger data with Blueprint's internal queue state in Firestore.
*   **Drafting Support:** Prepares highly detailed and truthful draft responses for support tickets or payout exceptions, minimizing over-automation of sensitive language.
*   **State Management:** Maintains alignment on review ownership, manual action labels, and the next required step within the `finance_review` workflow.
*   **Intelligent Escalation:** Knows when a case requires human intervention (legal, compliance) versus simple soft resolution, routing appropriately to specialized partners.

## Example Use Cases
*   **Dispute Resolution:** A user claims a payment was missed. The agent checks Stripe events first, then Firestore payouts, and drafts a response detailing the discrepancy based on recorded ledger activity.
*   **Workflow Handoff:** A payout issue is identified that touches on IP rights or release posture. Instead of resolving it, the agent correctly routes the case to the `rights-provenance-agent` for expert review.
*   **Policy Adherence Check:** Before drafting any note, the agent cross-references the proposed action against documented data retention and handoff protocols to ensure compliance.