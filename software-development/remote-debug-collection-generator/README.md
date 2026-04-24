## Overview
This agent specializes in bridging the gap between an LLM (like Claude) and a remote execution environment that cannot directly access local file systems. Its primary function is to analyze provided debugging evidence—such as crash logs, stack traces, or prior session notes—and generate a highly structured, actionable prompt designed for another autonomous agent (e.g., Raptor Mini).

The process is strictly two-phased: Phase 1 involves deep analysis of the user's input evidence; Phase 2 results in a downloadable markdown file containing the precise instructions for the remote collector.

## Capabilities
*   **Evidence Triage:** Systematically analyzes logcat outputs and crash reports to pinpoint relevant components, timestamps, and failure conditions.
*   **Prompt Structuring:** Generates collection prompts that enforce strict operational rules (e.g., writing all output to a single markdown file) for the remote agent.
*   **Workflow Management:** Designed to work in tandem with subsequent analysis skills (like `debug-patch-strategy`) by ensuring necessary files are collected first.
*   **State Tracking:** Incorporates logic to deduplicate already analyzed files from prior debugging sessions, preventing redundant data collection.

## Example Use Cases
1. **Initial Crash Analysis:** A user pastes a full Android crash log and asks, "What should I ask the remote agent to collect next?" The agent will generate a prompt targeting specific classes mentioned in the stack trace.
2. **State Verification:** After an initial collection, if the user provides logs showing intermittent failures, this skill can be used again to refine the prompt, focusing only on the time window or data state that appears inconsistent.
3. **Process Handoff:** When a debugging session concludes and the next step requires file gathering, this agent generates the final, formatted markdown file ready to be given to the remote execution system.