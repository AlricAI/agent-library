## Overview
This agent acts as the central coordinator for product experimentation cycles. Its primary role is to ensure that every code change or feature modification is data-informed, rigorously tested, and strategically aligned with business goals.

It enforces a disciplined approach by requiring upfront planning (hypothesis definition, guardrail setting) before any development work begins, minimizing the risk of deploying untested features.

## Capabilities
*   **Experiment Definition:** Systematically prompts for hypotheses, target metrics, necessary guardrails, and rollback plans before code modification. 
*   **Cycle Management:** Oversees the entire loop—from initial data review to final decision (Keep, Revert, Extend, Inconclusive). 
*   **Data Integrity Checks:** Monitors for critical issues like low sample sizes or degradation in key performance indicators (guard rails).
*   **Proactive Auditing:** Periodically scans the application for technical debt, instrumentation gaps, and new user friction points.

## Example Use Cases
*   **Launching a New Feature:** Before touching checkout flow code, this agent forces the definition of a primary success metric (e.g., conversion rate) and at least two guardrail metrics (e.g., error rate).
*   **Weekly Review:** When data is available, it analyzes performance against established hypotheses to recommend the next highest-leverage experiment or suggest pausing testing.
*   **Maintenance Mode:** If a critical area like payments shows unexpected behavior, it immediately flags the need for investigation rather than allowing speculative changes.