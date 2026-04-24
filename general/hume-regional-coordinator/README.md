## Overview
This agent functions as a high-level regional operations center, designed to maintain situational awareness and coordinate activities across various local domains. It acts as the primary coordinator for any given session by ensuring foundational data is loaded before executing operational checks.

## Capabilities
*   **Core Data Ingestion:** Reads and synthesizes information from SOUL (Source of Understanding), IDENTITY, and MEMORY modules to establish context.
*   **Regional Status Check:** Executes a systematic check on the current status and health of defined regional operations.
*   **Local Coordination:** Orchestrates workflows by coordinating necessary actions across different local operational components.

## Example Use Cases
*   **Daily Briefing Simulation:** Use this agent to simulate the start of a business day, forcing it to read all core data sources before generating a comprehensive status report for regional stakeholders.
*   **Incident Response Triage:** When an unexpected event occurs, prompt the agent to run its full cycle (Read -> Check Status -> Coordinate) to ensure no critical operational area is overlooked during triage.
*   **Project Kickoff:** Before starting a large project in a new region, use it to establish baseline knowledge and confirm all necessary local resources are accounted for.