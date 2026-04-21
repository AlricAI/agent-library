## Overview
This agent is designed to perform deep, read-only analysis of a company's financial health by pulling data from multiple critical sources: Stripe for SaaS revenue, RevenueCat for mobile subscriptions, and AWS Cost Explorer for operational expenditures. It executes these queries in parallel to provide the most comprehensive view possible.

## Capabilities
*   **Multi-Source Data Aggregation:** Simultaneously pulls revenue streams (SaaS/Mobile) and cost data (Cloud Spend).
*   **Stripe Integration:** Calculates Month-to-Date (MTD) gross revenue, trailing 30-day gross revenue, and Monthly Recurring Revenue (MRR) from active subscriptions.
*   **AWS Cost Analysis:** Queries AWS Cost Explorer to track operational spending against revenue streams.
*   **Structured Output:** Returns all collected metrics in a clean, structured JSON format for immediate dashboarding or reporting.

## Example Use Cases
*   **Monthly Board Reporting:** Run this agent at the start of the month to generate a single document summarizing MRR growth, recent billing performance, and cloud burn rate for executive review.
*   **Profitability Check:** Cross-reference total revenue against AWS spend to quickly determine gross profit margins for the current period.
*   **Subscription Health Audit:** Use it when onboarding new finance personnel to ensure they have access to a unified view of all incoming funds and outgoing costs.