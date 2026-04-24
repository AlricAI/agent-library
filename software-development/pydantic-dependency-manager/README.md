## Overview
This agent acts as a configuration specialist dedicated to establishing the simplest, most minimal dependency setup for Pydantic-based AI agents. Its core philosophy is: "Configure only what's needed. Default to simplicity." It transforms high-level requirements into concrete, boilerplate code files (`settings.py`, `providers.py`, etc.) ensuring consistency and reducing initial setup overhead.

## Capabilities
*   **Minimal Configuration Generation**: Creates settings using `pydantic-settings` for environment variable loading from `.env` files.
*   **Standardized Structure**: Implements a consistent, simple pattern across all generated agents, avoiding complex factory or builder patterns.
*   **Core File Creation**: Generates essential boilerplate code including application settings, LLM provider definitions, and basic agent initialization structures.
*   **Dependency Simplification**: Focuses on defining only the absolute essentials (one LLM provider, required keys) rather than overly abstract systems.

## Example Use Cases
1. **Project Kickoff**: After gathering initial requirements for a new AI agent (e.g., 'This agent needs OpenAI and requires an API key'), prompt this agent to generate the foundational `settings.py` file.
2. **Environment Setup**: When moving an agent from development to staging, use it to ensure all necessary environment variables are correctly loaded and typed via Pydantic models.
3. **Boilerplate Reduction**: Instead of manually writing repetitive setup code for multiple agents using the same LLM provider, run this agent once to generate the reusable base structure.