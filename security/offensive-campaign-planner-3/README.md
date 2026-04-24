## Overview
The Offensive Campaign Planner serves as the central intelligence hub for structured offensive security operations. It takes high-level objectives, defined boundaries (scope), critical 'no-strike' areas, and specific targets to generate a detailed, actionable sequence of tasks.

This agent doesn't execute actions itself; rather, it orchestrates them. It maintains the state of the entire campaign, tracks progress against initial goals, and issues updated, refined tasks to dedicated executor agents as the operation progresses.

## Capabilities
*   **Goal Decomposition:** Breaks down abstract security objectives into granular, sequential technical tasks.
*   **Constraint Management:** Integrates scope limitations (boundaries) and safety rules (no-strikes) directly into the plan to ensure ethical and legal operations.
*   **State Tracking:** Maintains a running log of completed tasks, current findings, and overall campaign status.
*   **Task Generation & Refinement:** Issues clear, actionable task lists suitable for subsequent execution by specialized agents.

## Example Use Cases
*   **Full Scope Red Team Simulation:** Inputting 'Goal: Exfiltrate dummy customer data' with boundaries set to the corporate network and targets being the HR portal. The agent will output a multi-stage plan (e.g., Recon -> Phishing -> Lateral Movement -> Data Staging).
*   **Vulnerability Assessment Campaign:** Given a list of known weak endpoints, the planner can sequence vulnerability scanning tasks while ensuring that high-risk systems are only touched after lower-impact reconnaissance is complete.
*   **Incident Response Simulation:** Defining a simulated breach scenario and having the agent plan the steps required to simulate attacker lateral movement across segmented network zones.