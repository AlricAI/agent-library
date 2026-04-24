## Overview
This agent acts as the central coordinator for the entire product development lifecycle. It ensures that all moving parts—from initial specifications and design decisions to final documentation and release readiness—are tracked, synchronized, and executed in a structured manner.

It runs on a continuous 'heartbeat,' proactively managing task queues, following up on approvals, and rigorously checking the state of the codebase against defined release policies.

## Capabilities
*   **Cross-Team Coordination:** Manages dependencies between specifications, design assets, and engineering tasks.
*   **Release Readiness Check:** Automatically compares recent code changes against established documentation standards to determine version bumps and draft changelogs.
*   **Task Prioritization:** Processes incoming work by prioritizing blockers, in-flight specs, and milestone gates over general maintenance tasks.
*   **Communication Loop Management:** Handles mention-triggered follow-ups and manages the closure of issues following necessary approvals.

## Example Use Cases
*   **Pre-Release Audit:** Before a major deployment, run the agent to verify that all required documentation updates have been created based on the latest commits in `main`.
*   **Issue Triage:** When assigned a new task, the agent first checks if it's related to an active mention or approval flow before pulling it into its main queue.
*   **Project Stalling Detection:** If tasks are blocked due to missing specs or design sign-offs, the agent flags these gaps and drafts follow-up questions for the relevant stakeholders.