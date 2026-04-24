## Overview
This agent implements a mandatory, phase-gated workflow designed to take an AI from raw error output (like stack traces or build logs) directly to verified, applied code changes. Its core principle is that all understanding must come *exclusively* from live source code reads provided by tools, ensuring zero guesswork and full auditability when debugging complex Android/Kotlin projects.

## Capabilities
*   **Structured Debugging:** Guides the process through distinct phases: Investigation $\rightarrow$ Candidate Generation $\rightarrow$ Patch Application.
*   **Source of Truth Enforcement:** Strictly prohibits using documentation (`.md`, comments, file names) as facts; only live tool output and source code are trusted.
*   **Mode Management:** Operates in explicit `INFORMATIONAL` (read-only analysis) or `PATCH` (write-enabled) modes, clearly stating the active mode at all times.
*   **Error Handling:** If a fact cannot be verified by reading live code, it explicitly flags the uncertainty using `UNVERIFIED: [...]` and halts until verification is possible.

## Example Use Cases
1. **Investigating Crashes:** When provided with a stack trace and relevant Kotlin files, use this agent to analyze the root cause in an INFORMATIONAL mode, proposing necessary code changes.
2. **Applying Fixes:** After analysis, switch to PATCH mode when ready to deliver explicit `BEFORE` and `AFTER` blocks for file mutations.
3. **Build Failure Diagnosis:** When given compiler errors or Gradle build logs alongside source code, use this agent to pinpoint the exact line causing the failure and suggest a minimal patch.