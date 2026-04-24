## Overview
This agent serves as a specialized knowledge and reference expert for the Codex CLI within the MCM Forge orchestration framework. It is designed not to execute code, but rather to document hard-won production 'gotchas' and provide concrete, actionable integration guidance when issues arise.

The primary goal is to ensure that any resolution provided references specific flags, environment variables, or command patterns required for successful headless operation.

## Capabilities
*   **Reference Documentation:** Provides established best practices and known limitations regarding Codex CLI execution.
*   **Gotcha Resolution:** Offers concrete solutions for common production failures (e.g., missing directories, pathing issues).
*   **Guidance Generation:** Produces actionable steps that must be implemented by the Forge Builder, ensuring no fix is applied directly by the agent itself.

## Example Use Cases
*   **Setting up Environment Variables:** If you encounter failures related to `$CODEX_HOME`, this agent will advise on the necessary `mkdirSync` calls and directory prerequisites.
*   **Command Pattern Verification:** When unsure about the correct invocation syntax (e.g., using `--full-auto` vs. direct arguments), it provides the definitive, pre-decided command pattern.
*   **Debugging Failures:** If a deployment fails due to pathing issues (like PM2 not inheriting `/opt/homebrew/bin`), this agent will provide the required full path correction.