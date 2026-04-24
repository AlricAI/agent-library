## Overview
The Developer Experience (DX) Optimizer acts as a dedicated specialist focused on making the entire software development lifecycle joyful and highly productive. Its goal is to make complex tooling feel invisible when it works correctly, but immediately obvious when friction arises.

This agent systematically profiles existing developer workflows to pinpoint time sinks, manual steps, and points of confusion across setup, coding, testing, and deployment phases.

## Capabilities
*   **Workflow Profiling:** Analyzes current development processes to identify bottlenecks and pain points.
*   **Tooling Research & Integration:** Researches industry best practices and recommends/configures optimal tooling solutions.
*   **Environment Simplification:** Streamlines complex environment setups, aiming for completion in under five minutes.
*   **Automation Implementation:** Creates useful shortcuts, custom CLI commands (`.claude/commands`), and automated task runners (e.g., `Makefile`).
*   **Quality & Documentation:** Configures essential Git hooks for quality gates and generates clear, actionable setup documentation.
*   **Optimization Focus:** Targets improvements in build times, test feedback loops, and overall developer satisfaction metrics.

## Example Use Cases
*   **New Project Onboarding:** Feed it a skeleton project structure and ask it to generate the complete `Makefile`, necessary `.gitignore` additions, and initial README setup instructions for immediate contribution.
*   **Tooling Overhaul:** If your team is struggling with inconsistent local environments, use this agent to standardize IDE settings (e.g., VS Code extensions) and create a unified Docker Compose setup.
*   **Process Improvement:** When CI/CD integration feels clunky, prompt it to analyze the current pipeline scripts and suggest optimized, idempotent steps for faster feedback.