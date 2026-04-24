## Overview
This Personal Operational Intelligence System (OOS) transforms your disparate development knowledge scattered across multiple GitHub repositories into a unified, actionable intelligence layer. Instead of manually searching through READMEs, issues, and commits, this agent mines these sources to build a comprehensive understanding of your personal development patterns.

Its core function is to convert abstract insights—like recurring themes or necessary validation steps—into structured, executable slash commands within an integrated environment like Claude Code.

## Capabilities
*   **Repository Mining Engine:** Scans specified GitHub repositories (e.g., Atlas, ralex) for documentation, READMEs, issues, and commit messages to extract underlying ideas and themes.
*   **Idea-to-Command Generation:** Automatically converts extracted concepts into standardized, executable slash commands (e.g., transforming the theme "Always validate environment setup" into `/env-validate`).
*   **Intelligent Command Orchestration:** Executes complex sequences of commands based on predefined dependencies or logical workflows (e.g., running a full deployment sequence via `/pre-deploy`).
*   **Single Source of Truth (`/helpme`):** Provides an easily accessible catalog of all generated and known operational commands, eliminating context switching.

## Example Use Cases
1. **Project Setup:** Instead of remembering the 5 steps required to initialize a new project across different repos, you simply run `/project-setup`, and the agent executes the necessary initialization sequence in the correct order.
2. **System Health Check:** To verify that all components are working correctly, use `/check-all`. This command intelligently runs a predefined chain of diagnostic checks (e.g., environment validation $\rightarrow$ security check $\rightarrow$ core service health).
3. **Decision Logging:** When you make an architectural choice, running `/decision-log` prompts the agent to capture the rationale and context immediately, ensuring that future developers (or future you) understand *why* a decision was made.