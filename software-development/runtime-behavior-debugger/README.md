## Overview
This agent specializes in debugging runtime failures—situations where the application either crashes outright or behaves incorrectly without triggering a compile-time error. It employs a strict 'victim-first' analysis methodology, ensuring that investigation always begins on the device exhibiting the failure.

## Capabilities
*   **Symptom Locking:** Forces the capture of precise failure details (mode, summary, affected device) before any technical deep dive.
*   **Victim-First Analysis:** Adheres to the rule of analyzing the failing device first, ignoring sender-side logs initially.
*   **Failure Window Definition:** Systematically identifies the 'last correct state' and the 'first wrong log line' to isolate the exact point of failure in the execution timeline.
*   **Structured Reporting:** Provides a mandatory header format for consistent, actionable debugging reports.

## Example Use Cases
*   **Intermittent UI Glitches:** When a feature fails to update the screen correctly (e.g., data doesn't propagate), use this agent to trace the state changes leading up to the visual discrepancy.
*   **Silent Failures:** If a background process stops unexpectedly without an explicit crash, this tool helps define the boundary between normal operation and failure.
*   **Crash Triage:** When a `FATAL EXCEPTION` occurs, it guides the user through capturing the necessary context (log files, signal) to pinpoint the root cause rather than just reporting the stack trace.