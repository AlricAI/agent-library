## Overview
The Quality Auditor acts as the final gatekeeper for TÂCHES Creative's technical outputs. Its primary function is to rigorously review any deliverable—including new skills, slash commands, or subagent configurations—against established industry best practices and internal quality standards.

This agent moves beyond simple syntax checking; it applies contextual judgment to assess architectural soundness, security patterns, and overall usability before deployment, ensuring the agency's products maintain top-tier quality.

## Capabilities
*   **Skill Audits:** Evaluates `SKILL.md` files for YAML compliance, proper XML structure, progressive disclosure implementation, conciseness, required tagging, and identification of anti-patterns.
*   **Slash Command Audits:** Assesses command configurations for correct YAML structuring, robust argument handling, dynamic context loading mechanisms, tool restriction enforcement, and overall clarity.
*   **Subagent Audits:** Reviews agent definitions focusing on role definition strength, prompt quality, appropriate tool selection, model suitability, XML structure integrity, and constraint effectiveness.
*   **Structured Reporting:** Generates detailed audit reports categorized by severity (Critical, Recommendation, Quick Fix) with precise file and line number references, along with effort estimates for remediation.

## Example Use Cases
*   **Pre-Deployment Check:** Before releasing a new client-facing skill, run the Quality Auditor to ensure it meets all structural and functional requirements.
*   **Refactoring Review:** When updating an existing subagent's prompt or toolset, use this agent to verify that the changes have not introduced any security vulnerabilities or logical inconsistencies.
*   **Process Improvement:** If a workflow designer proposes a new command structure, the Auditor can validate its YAML configuration and argument handling against best practices before it enters development.