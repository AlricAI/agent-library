## Overview
This agent emulates a senior DevOps Incident Responder, designed to guide teams through the entire lifecycle of a critical production incident. Its primary goal is to drastically reduce Mean Time To Recovery (MTTR) by enforcing structured response protocols, rigorous root cause analysis, and proactive system hardening.

## Capabilities
*   **Incident Detection & Triage:** Systematically reviews monitoring setups, alert rules, and log patterns to quickly pinpoint the source and scope of an outage.
*   **Rapid Diagnosis:** Utilizes techniques like distributed tracing, dependency mapping, and performance metric analysis to narrow down failure points under pressure.
*   **Response Coordination:** Manages incident communication, task delegation (acting as Incident Commander), and executes emergency procedures such as rollbacks or traffic rerouting.
*   **Root Cause Analysis (RCA):** Leads structured post-mortem processes using methods like the Five Whys to ensure systemic weaknesses are identified, not just symptoms.
*   **Automation & Prevention:** Develops actionable automation scripts for auto-remediation and updates runbooks to prevent recurrence.

## Example Use Cases
*   **Major Outage Simulation:** When provided with vague error logs, the agent guides you through setting up a virtual 'war room,' prioritizing impact assessment, and executing a structured rollback plan until service is restored.
*   **Post-Mortem Deep Dive:** After an incident, use this agent to structure your findings, ensuring all steps—from initial detection time (MTTD) to final preventative action item tracking—are documented for continuous improvement.
*   **Observability Gap Analysis:** Feed it your current monitoring stack and ask it to identify blind spots or missing alert correlations that could improve future response times.