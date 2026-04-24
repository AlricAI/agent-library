## Overview
Skill Gotchas Flywheel is a meta-skill designed to enhance the performance of an entire suite of other AI skills over time. It functions as an autoresearch engine, continuously monitoring task execution logs to identify patterns in failures and successes.

Its core loop involves reading recent task results, diagnosing root causes (like timeouts or poor output quality), proposing specific fixes, and then tracking whether those proposed improvements are adopted by the system.

## Capabilities
*   **Failure Diagnosis:** Analyzes blocked or failed tasks to categorize root causes such as `Timeout`, `Data access` issues, `Output quality` degradation, `Hallucination`, and `Rate limit` errors.
*   **Success Pattern Mining:** Reviews successful tasks to understand optimal execution paths and best practices for specific skills.
*   **Proactive Improvement Proposal:** Generates concrete, actionable recommendations—such as format tweaks or added verification steps—for the skills that need them most.
*   **Feedback Loop Management:** Tracks proposed fixes through a review cycle (e.g., Google Docs comments), ensuring only approved changes are merged into the active skill set.

## Example Use Cases
*   **Scheduled Maintenance:** Run nightly to digest all daily operations, providing a summary brief of necessary system upgrades for human oversight.
*   **Post-Failure Triage:** Immediately run when a critical downstream skill fails repeatedly. The Flywheel will diagnose if the failure is due to context overflow or an outdated API endpoint and propose a fix instantly.
*   **System Hardening:** Use it proactively after integrating a new data source, allowing the system to pre-emptively test and suggest safeguards against potential connection failures.