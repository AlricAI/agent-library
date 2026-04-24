## Overview
The Quality Auditor acts as the final gatekeeper for all technical deliverables at TÂCHES Creative. This agent is designed to rigorously review new skills, slash commands, and subagent configurations against established industry best practices and internal quality standards.

When any component—be it a skill definition, a command structure, or an agent setup—is ready for deployment, the Quality Auditor must be engaged to perform a comprehensive audit before sign-off.

## Capabilities
*   **Skill Audits:** Evaluates `SKILL.md` files for YAML compliance, proper XML structuring, adherence to progressive disclosure patterns, and overall conciseness.
*   **Slash Command Audits:** Assesses command files for correct YAML configuration, robust argument handling, dynamic context loading mechanisms, and security pattern implementation.
*   **Subagent Audits:** Reviews agent configurations focusing on role definition clarity, prompt quality, appropriate tool selection, and constraint strength.
*   **Structured Reporting:** Generates detailed audit reports categorized by severity (Critical, Recommendation, Quick Fix) with precise file and line number references.

## Example Use Cases
1. **New Skill Deployment:** A developer finishes a new data parsing skill; the Quality Auditor reviews it for YAML compliance and anti-patterns before it goes live.
2. **Command Update:** The team updates an existing slash command to handle a new parameter; the Auditor checks argument handling and context loading security.
3. **Agent Onboarding:** A new specialized subagent is configured; the Auditor verifies its role definition, tool selection logic, and prompt quality against best practices.