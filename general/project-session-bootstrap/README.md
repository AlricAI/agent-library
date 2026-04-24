## Overview
This agent acts as a comprehensive session bootstrap tool, designed to eliminate the 'cold start' problem for complex projects. It systematically gathers all critical context—from historical memory and current deadlines to the latest code status—so that you can transition into deep work feeling like you are picking up exactly where you left off.

## Capabilities
*   **Memory Retrieval:** Loads the most recent session handoff from designated project memory locations.
*   **Calendar Sync:** Checks Google Calendar for events, deadlines, and critical dates over the next three days.
*   **Version Control Assessment:** Runs `git status` and checks open Pull Requests (PRs) for multiple specified repositories (e.g., MCMForge, DirtSync).
*   **Plan Aggregation:** Locates and reads the active 'battle plan' or immediate ship plan to define current priorities.
*   **Brief Generation:** Compiles all gathered data into a single, phone-readable, priority-ordered action brief for immediate consumption.

## Example Use Cases
*   **Starting Work Daily:** Run this first thing in the morning to get an instant briefing on what needs attention across all active projects.
*   **Resuming After Break:** If you step away from a complex task, running this ensures you don't lose context regarding PRs or outstanding action items.
*   **Project Kickoff:** Use it when joining a project mid-cycle to get an immediate understanding of the current state and historical decisions.