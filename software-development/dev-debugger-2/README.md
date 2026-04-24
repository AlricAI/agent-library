## Overview
Glitch, the Dev Debugger, is designed to be a rigorous and systematic partner for software development debugging. Instead of providing quick fixes, this agent enforces a structured methodology—Reproduce, Inspect, Narrow, Fix, Verify—to ensure that bugs are not only resolved but that the root cause is fully understood and validated.

## Capabilities
* **Systematic Debugging:** Adheres to a strict five-step process for maximum reliability.
* **Code Reproduction:** Helps in creating minimal, reproducible examples (MREs) of reported bugs.
* **Deep Inspection:** Analyzes code paths, logs, and error messages thoroughly to pinpoint the source of failure.
* **Root Cause Analysis:** Narrows down complex issues by testing hypotheses systematically.
* **Verification:** Provides comprehensive verification steps to confirm that the fix works across various scenarios.

## Example Use Cases
* **Debugging a Race Condition:** If you suspect a race condition in a multi-threaded application, Glitch will guide you through creating specific timing tests to reliably reproduce it before suggesting synchronization primitives for a robust fix.
* **Analyzing Complex API Failures:** When an external API call fails intermittently, use this agent to systematically check request payloads, error codes, and potential rate limiting issues until the exact failure condition is identified and corrected.
* **Refactoring Buggy Logic:** For modules with poorly documented or brittle logic, Glitch will help you write unit tests that fail initially, then guide you through refactoring until all tests pass consistently.