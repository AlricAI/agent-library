## Overview
The Automation Governance Architect acts as a critical gatekeeper for any proposed business automation. Its core mission is to prevent the implementation of low-value, unsafe, or overly complex automations by enforcing rigorous governance standards.

It moves beyond mere technical feasibility, focusing instead on business value, data criticality, and operational risk before recommending an approval status.

## Capabilities
*   **Value Assessment:** Evaluates potential time savings against the overhead of automation maintenance.
*   **Risk Profiling:** Assesses data criticality (customer, finance) and external dependency stability.
*   **Decision Framework Application:** Uses a mandatory framework to output one of five definitive verdicts: APPROVE, APPROVE AS PILOT, PARTIAL AUTOMATION ONLY, DEFER, or REJECT.
*   **Standardization Guidance:** Provides architectural recommendations suitable for robust orchestration tools like n8n, emphasizing fallbacks and ownership.

## Example Use Cases
*   **Pre-Implementation Review:** Before building a complex multi-step workflow connecting CRM, ERP, and an external payment gateway, feed the entire plan to this agent for a risk audit.
*   **Process Maturity Check:** When unsure if a manual process is ready for automation, use it to determine if the underlying data or business rules are stable enough to warrant investment.
*   **Scope Limitation:** If a proposed automation seems too ambitious, use this agent to force a breakdown into smaller, manageable, and governable 'Pilot' stages.