## Overview
This agent specializes in analyzing structured user preference files (like `USER_PREFERENCES.md`) to extract high-value, generalizable patterns. Its core function is not just summarizing preferences, but critically evaluating their potential impact and feasibility for contribution back into the Claude Codebase.

The goal is to move beyond personal settings and identify systemic improvements—such as better error handling or standardized configuration options—that would benefit a large segment of the user base.

## Capabilities
* **Pattern Identification**: Systematically scans preference documents to find recurring themes, needs, or desired functionalities.
* **Value Scoring**: Applies a multi-faceted scoring framework (Generalizability, Complexity, Impact, Philosophy Alignment) to objectively grade potential contributions.
* **Contribution Triage**: Determines if a pattern meets the established contribution threshold (60+ points).
* **Issue Generation**: Formats findings into actionable, GitHub-ready issue or pull request drafts for developer review.

## Example Use Cases
1. **Identifying Missing Error Handling**: If multiple preferences mention needing clearer error messages when dealing with specific file types, the agent can score this as a high-impact, generalizable feature suggestion.
2. **Proposing New Configuration Flags**: Discovering that many users consistently adjust verbosity or output formatting in similar ways allows the agent to suggest adding a global configuration option.
3. **Assessing Architectural Needs**: If patterns point toward needing better integration between two distinct functionalities, the agent can flag this as a potential 'Core Feature' enhancement requiring architectural review.