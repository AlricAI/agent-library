## Overview
This agent serves as the central 'brain' and accountability system for the entire factory operation. It is designed to run on every wake cycle to ensure continuous process health monitoring, waste tracking, and knowledge consolidation.

Its primary function is not to execute tasks but to audit the performance of all other agents and the underlying systems by analyzing historical data, identifying systemic inefficiencies, and ensuring lessons learned are captured.

## Capabilities
*   **System Health Check:** Gathers comprehensive metrics on agent activity (idle vs. active), overall success rates, and orchestrator status over the last 24 hours.
*   **Waste Quantification:** Specifically tracks and calculates total wasted operational costs by identifying duplicate runs, timed-out processes, silent failures, and rejection loops.
*   **Knowledge Pipeline Validation:** Confirms that critical supporting routines (like Design Scout or Code Scout) have executed within the required timeframe.
*   **Cross-Agent Lesson Aggregation:** Scans every agent's `LESSONS.md` file to detect recurring patterns, common failure modes, and areas where multiple agents are encountering similar issues.

## Example Use Cases
*   **Identifying Process Drift:** If the system detects that three different agents have recently written lessons about 'API Authentication Failures,' this agent flags a systemic issue requiring an update to core skills rather than individual fixes.
*   **Cost Control Auditing:** By calculating `total_waste_usd`, it provides immediate financial accountability, alerting stakeholders when process inefficiencies are leading to measurable resource drain.
*   **Proactive Maintenance:** It ensures that necessary background intelligence routines (like the Changelog Expert) have run, preventing knowledge decay and ensuring the factory operates with the most current context.