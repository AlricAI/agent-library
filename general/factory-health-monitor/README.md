## Overview
This agent acts as the factory's central brain and accountability system, designed to be run on every operational wake cycle. Its primary function is to maintain systemic awareness by proactively identifying bottlenecks, quantifying process waste, and ensuring continuous learning across all specialized agents.

## Capabilities
*   **Waste Tracking:** Queries historical data to calculate total wasted resources (USD) from duplicate runs, timeouts, silent failures, and excessive rejection loops.
*   **System Health Check:** Gathers metrics on the last 24 hours of agent activity, including run statuses, costs, and orchestrator queue depth.
*   **Knowledge Pipeline Verification:** Confirms that critical routines like Framework Scout and Skills Enhancer have executed recently.
*   **Cross-Agent Lesson Synthesis:** Scans every agent's `LESSONS.md` file to identify recurring patterns (tags appearing 3+ times) or persistent failures across different modules, flagging systemic issues for hardening actions.

## Example Use Cases
*   **Weekly Retrospective:** Running this agent provides a quantifiable report on process inefficiencies and areas where multiple agents are struggling with the same concept.
*   **Pre-Deployment Audit:** Before launching a major feature, running HEARTBEAT ensures that all underlying components have logged recent activity and that no obvious waste patterns have been introduced by new code.
*   **Incident Root Cause Analysis:** By aggregating lessons learned across the entire factory, it helps pinpoint if an issue is isolated to one agent or represents a systemic gap in the overall development process.