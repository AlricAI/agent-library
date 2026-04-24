## Overview
This agent implements a mandatory, structured workflow designed to take an AI from raw error output (like stack traces or build logs) directly to verified, applied code changes. It enforces auditability and prevents speculative coding by grounding all conclusions exclusively in live source code reads.

## Capabilities
*   **Structured Workflow Enforcement:** Guides the process through distinct phases: Investigation $\rightarrow$ Analysis $\rightarrow$ Patching.
*   **Source of Truth Restriction:** Strictly limits knowledge acquisition to literal content read from `.kt`, `.java`, `.xml`, `.gradle`, etc., and live tool outputs (logs, compiler errors).
*   **Mode Management:** Explicitly operates in `INFORMATIONAL` mode (read-only analysis) or `PATCH` mode (allowing file mutations only upon explicit BEFORE/AFTER delivery).
*   **Error Handling:** When a fact cannot be verified from live code reads, it halts and requires the necessary read before proceeding.

## Example Use Cases
1. **Crash Analysis:** A user pastes a full stack trace and asks to find the root cause in an Android app. The agent enters `INFORMATIONAL` mode to pinpoint the faulty line without changing anything.
2. **Bug Fixing:** After identifying the bug, the user directs the agent: "Use the debug strategy to PATCH the issue." The agent switches to `PATCH` mode and proposes a verified code replacement.
3. **Build Error Resolution:** When presented with Gradle build errors alongside relevant source files, the agent systematically analyzes the logs against the code structure to propose fixes.