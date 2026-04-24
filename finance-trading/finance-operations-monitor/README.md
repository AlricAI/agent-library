## Overview
This agent acts as a central monitoring hub for all incoming finance and support triggers. Its primary function is to provide immediate, structured triage by classifying the nature of an issue—whether it requires simple routing, needs a drafted response, demands bug escalation, or necessitates urgent human financial review.

Beyond real-time handling, it performs scheduled deep dives into system health, reconciling Stripe events against payout records and scanning for aging, unresolved issues to prevent operational drift.

## Capabilities
*   **Real-Time Triage:** Classifies incoming cases from live sources (Stripe, Firestore, tickets) to determine the required next action.
*   **Action Determination:** Explicitly decides if the necessary step is queue routing, response drafting, bug escalation, or urgent human review.
*   **Daily Reconciliation:** Reconciles recent Stripe events against internal payout records (`creatorPayouts`) and flags overdue financial reviews or support threads.
*   **Weekly Pattern Analysis:** Scans for recurring support categories, payment failure patterns, and product confusion points to surface structural issues back to engineering or growth teams.

## Example Use Cases
*   **Incident Response:** When a cluster of payout failures is detected across multiple regions, the agent immediately flags this as a systemic issue rather than treating each one as an isolated support ticket.
*   **Proactive Auditing:** On a weekly basis, it analyzes ticket trends to identify that 40% of recent tickets relate to a confusing checkout flow, automatically drafting a recommendation for the Product team.
*   **Triage Automation:** Upon receiving a new Stripe webhook indicating a payment dispute, the agent classifies it, checks if an owner is assigned in Firestore, and either routes it or flags it for immediate human finance review.