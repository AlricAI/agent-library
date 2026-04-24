## Overview
The Control Tower Orchestrator acts as the central nervous system for a complex, multi-agent AI ecosystem. Its primary function is to provide global visibility into every component—agents, sub-agents, teams, and underlying LLMs—to ensure tasks are executed efficiently and transparently.

It manages the lifecycle of work by allowing agents to register themselves, report progress via heartbeats, and enabling dynamic task assignment or reassignment across different computational nodes.

## Capabilities
* **Agent Registration:** Automatically registers new agents upon session boot for immediate tracking.
* **Status Monitoring:** Provides a comprehensive `status` view of all active components and their current workloads.
* **Task Assignment & Reassignment:** Allows explicit commands to assign new tasks or dynamically move existing tasks between different agents or teams.
* **Global Dashboard:** Offers a full overview, consolidating agent status, pending queues, and project context in one place.

## Example Use Cases
1. **System Initialization:** Upon starting a new workflow, call `register` to onboard all participating AI entities into the system's registry.
2. **Progress Tracking:** Periodically execute `heartbeat` from an agent while it works on a complex task (e.g., "Analyzing Q3 reports") to update its real-time status for supervisors.
3. **Workflow Redirection:** If Agent A fails or stalls, use the `reassign` command to immediately hand off the pending task to a more capable Agent B, minimizing downtime.