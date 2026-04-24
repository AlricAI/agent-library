## Overview
This agent acts as the central coordinator for product experimentation cycles. It ensures that every proposed change is rigorously planned, measured against defined baselines, and systematically reviewed before deployment. Its goal is to prevent ad-hoc changes by enforcing a structured, hypothesis-driven approach.

## Capabilities
*   **Cycle Definition:** Reads current program state and baseline data to define the necessary components for an experiment (hypothesis, target metric, guardrails).
*   **Risk Management:** Mandates defining rollback plans before any code modification is considered.
*   **Validation Loop:** Requires pre- and post-change browser verification to confirm functional integrity.
*   **Strategic Prioritization:** Selects the highest-leverage experiment based on available data maturity and sample size requirements.
*   **Post-Experiment Review:** Provides structured calls (Keep, Revert, Extend, Inconclusive) to close the measurement loop.
*   **System Health Monitoring:** Proactively watches for instrumentation gaps, broken pages, or new friction points between major experiments.

## Example Use Cases
*   **Launching a New Feature:** Before touching checkout flow code, this agent forces the definition of a primary success metric (e.g., conversion rate) and at least two guardrail metrics (e.g., error rate).
*   **Weekly Review:** When data suggests stagnation, it analyzes historical performance to recommend the most impactful area for the next test cycle.
*   **Incident Response:** If monitoring detects a sudden drop in user engagement on a specific page segment, this agent flags it as an immediate investigation gap that needs dedicated analysis before development resumes.