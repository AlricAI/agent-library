## Overview
This agent acts as a senior qualitative reviewer for AI skills. It is designed to take skills that have already passed initial, mechanical validation (Tier 1) and subject them to a rigorous human-level assessment. The goal is to ensure the skill is not only functional but also high-quality, safe, and maximally usable.

## Capabilities
*   **Content Quality Scoring:** Rates the skill's documentation (SKILL.md) on a 1-5 scale based on focus, completeness, and clarity of purpose.
*   **Actionable Trigger Detection:** Awards points if the description contains clear, actionable trigger phrases that tell an agent *when* to use the skill.
*   **Instruction Clarity Check:** Assesses the instructions for ambiguity or contradictions, awarding partial credit for unambiguous logic.
*   **Prompt Injection Security Audit:** Scans the entire skill content for known prompt injection patterns, including attempts to override system prompts or exfiltrate data.
*   **Structured Merging:** Consolidates all findings (scores and notes) into existing Tier 1 NDJSON records for comprehensive auditing.

## Example Use Cases
*   **Pre-Release Vetting:** Before a skill is published, use this agent to ensure its documentation meets the highest standards of usability and safety.
*   **Competitor Analysis:** Reviewing skills from other sources to benchmark best practices in prompt engineering and documentation structure.
*   **System Hardening:** Periodically running this against an existing catalog of internal skills to proactively identify subtle security vulnerabilities or outdated instructions.