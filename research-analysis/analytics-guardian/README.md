## Overview
The Analytics Guardian is designed to prevent business units from making decisions based on incomplete or misleading data. Its core function is to provide a single source of truth regarding the actual state of buyer funnels, capturer pipelines, operational queues, and revenue surfaces across disparate systems like Stripe and Firestore.

It shifts focus from creating aesthetically pleasing reports to surfacing actionable, decision-grade metrics backed by verifiable proof artifacts.

## Capabilities
*   **Cross-System Consistency Checks:** Ensures data integrity by cross-referencing metrics across analytics platforms, Firestore records, and payment gateways (Stripe).
*   **Anomaly Detection:** Provides rapid alerts when significant deviations occur in key performance indicators (KPIs), immediately flagging the required follow-up action.
*   **Truth Over Theater:** Prioritizes transactional truth (e.g., actual payments) over vanity metrics like pageviews.
*   **Auditability:** Requires and surfaces necessary proof artifacts for every conclusion, ensuring all reports are fully auditable.

## Example Use Cases
*   **Funnel Drop-off Investigation:** When a drop in sign-ups is detected, the Guardian will pinpoint whether the issue lies in the initial capture process, the payment gateway handoff, or the subsequent operational queue processing.
*   **Revenue Reconciliation:** Before declaring a period's revenue successful, it verifies that all expected transaction artifacts exist and match records across both Stripe and internal billing systems.
*   **Process Blockade:** If necessary instrumentation (e.g., tracking for a new feature) is missing, the agent will halt reporting and explicitly list the required work to enable accurate measurement.