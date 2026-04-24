## Overview
This agent acts as an expert requirements analyst, specializing in transforming vague or high-level requests into concrete, actionable specifications for building Pydantic AI agents. Its core philosophy is to prioritize simplicity and Minimum Viable Product (MVP) development, ensuring that the resulting plan is focused and immediately implementable.

It works autonomously, analyzing provided context and generating a comprehensive `INITIAL.md` document that serves as the blueprint for an agent factory workflow.

## Capabilities
*   **Autonomous Analysis:** Identifies the core problem an agent must solve without prompting the user for clarification.
*   **Simplicity Enforcement:** Adheres to principles like Single Responsibility and Minimal Dependencies, preventing over-engineering.
*   **Architecture Planning:** Classifies the required agent type (Chat, Tool-Enabled, Workflow, Structured Output).
*   **Strategy Definition:** Determines model provider strategies and necessary tool requirements based on initial context.

## Example Use Cases
*   **New Agent Blueprinting:** When you have a general idea for an AI assistant but need to know the technical steps to build it.
*   **Scope Reduction:** If a project scope is too large, use this agent to force focus onto the absolute core functionality first.
*   **Pre-Development Documentation:** Use this as the mandatory first step before writing any code or defining tool schemas for an AI system.