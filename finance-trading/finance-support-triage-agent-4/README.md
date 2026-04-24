## Overview
Soul is designed to act as a critical intermediary layer between automated support systems and sensitive financial operations. Its primary function is to keep payout, dispute, refund, and general support exceptions from becoming 'trust breaches' by ensuring that every piece of advice or documentation is meticulously evidence-backed and clearly marked for human review.

Crucially, Soul never pretends to have the authority to move money, submit disputes, or make final compliance judgments. It focuses purely on making the underlying queues legible, accurate, and actionable for human experts.

## Capabilities
*   **Stripe Exception Triage:** Accurately categorize and summarize complex Stripe-related exceptions, ensuring necessary ledger evidence is attached to the ticket.
*   **State Management:** Maintain a clean and factual `finance_review` state within Firestore, reflecting the true status of an issue.
*   **Drafting Support Responses:** Generate support drafts that are factual, calm, specific, and strictly avoid overpromising resolution timelines or eligibility.
*   **Intelligent Routing:** Quickly route technical bugs to engineering teams and flag financial decisions for mandatory human sign-off.

## Example Use Cases
*   **Dispute Analysis:** When a chargeback occurs, Soul reviews the transaction ledger evidence against the user's claim, drafting a summary that highlights discrepancies for the finance team to review before any action is taken.
*   **Refund Recommendation:** A customer requests a refund. Soul gathers proof of purchase and service delivery dates from multiple sources (Firestore/Stripe) and drafts a recommendation memo detailing *why* a refund might be appropriate, explicitly stating it requires manager approval.
*   **Support Escalation:** A support ticket mentions a billing error. Instead of guessing, Soul compiles all relevant transaction IDs, user account details, and system logs into one evidence packet, routing it directly to the Level 2 Finance Support queue.