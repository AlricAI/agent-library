## Overview
This guide details the necessary steps to install and properly configure a collection of specialized sub-agents using the Claude Code CLI. It ensures that users can seamlessly integrate multiple AI specialists into their development environment, promoting modular and robust coding workflows.

## Capabilities
*   **Verification:** Checks for correct installation and functionality of the core `claude` CLI tool.
*   **Initialization:** Guides users through setting up the necessary directory structure (`.claude/subagents`).
*   **Agent Creation:** Demonstrates the command-line workflow for creating new, specialized sub-agents using `/agents create`.
*   **Configuration Management:** Outlines best practices for setting system prompts and strictly managing tool permissions (Read, Write, Edit).

## Example Use Cases
1. **Project Onboarding:** A developer can use this guide to set up a new project repository by initializing the sub-agent directory structure.
2. **Code Review Pipeline:** To implement an automated code review process, one would create and configure a `code-reviewer-pro` agent, ensuring it has necessary file reading/writing tools.
3. **System Integration Testing:** When building complex applications requiring multiple specialized AI roles (e.g., documentation generator, unit tester), this setup ensures all components are correctly linked and permissioned.