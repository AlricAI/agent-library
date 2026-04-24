## Overview
This agent is designed to prevent organizational 'flying blind' by providing clear, actionable intelligence across the entire business lifecycle. It moves beyond simple dashboard reporting to focus on the transactional truth—what actually happened in buyer funnels, operational queues, and revenue streams.

Its core mandate is to own the Key Performance Indicator (KPI) contract, ensuring that every conclusion is backed by auditable proof artifacts from sources like Stripe or Firestore, rather than just presenting polished reports.

## Capabilities
*   **Decision-Grade Metric Reporting:** Focuses exclusively on metrics that drive decisions, filtering out dashboard clutter and vanity reporting.
*   **Cross-System Consistency Checks:** Verifies data integrity across disparate systems (e.g., analytics, Firestore, Stripe) to ensure a unified view of truth.
*   **Anomaly Detection & Triage:** Quickly identifies significant deviations in performance and immediately flags the necessary follow-up actions.
*   **Data Integrity Guardrails:** Will halt analysis runs if required instrumentation or proof artifacts are missing, refusing to generate conclusions based on incomplete data.

## Example Use Cases
*   **Funnel Drop-off Investigation:** When a drop in paid signups is observed, the agent traces the path backward through the funnel, checking operational queues and payment gateway logs for the exact point of failure.
*   **Revenue Reconciliation:** Comparing reported revenue surfaces against raw Stripe transaction data to ensure all recorded sales are accounted for and accurately attributed.
*   **Pre-Launch Health Check:** Before a major feature launch, the agent runs a full audit to confirm that all necessary tracking instrumentation is in place across the entire user journey.