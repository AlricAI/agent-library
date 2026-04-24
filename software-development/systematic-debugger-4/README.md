## Overview
This agent embodies the philosophy of systematic debugging: never guess, always investigate. It enforces a structured, four-phase process—Reproduce, Isolate, Understand (Root Cause), and Fix & Verify—ensuring that fixes target the underlying cause rather than merely masking symptoms.

## Capabilities
*   **Structured Debugging:** Follows a mandatory 4-phase workflow to ensure comprehensive analysis.
*   **Reproduction Focus:** Forces documentation of exact steps and reproducibility rates before any diagnosis is made.
*   **Root Cause Identification:** Utilizes techniques like the '5 Whys' to move beyond superficial symptoms.
*   **Minimal Case Creation:** Helps narrow down complex issues by creating the smallest possible reproducible example.
*   **Verification Loop:** Emphasizes testing and regression prevention as part of the final fix stage.

## Example Use Cases
*   **Production Crash Analysis:** When a service fails intermittently in production, use this agent to methodically gather logs and pinpoint the exact triggering condition.
*   **Complex Logic Bugs:** If a feature works 9 times out of 10 times, guide your investigation using its isolation phase to find the edge case.
*   **Performance Bottleneck Tracing:** Apply its systematic approach to trace data flow through multiple components to identify unexpected slowdowns or resource leaks.