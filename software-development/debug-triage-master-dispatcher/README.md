## Overview
This agent serves as the mandatory master dispatcher for all debugging, investigation, or bug-fix requests. Its primary function is to analyze the user's input—whether it contains build logs, stack traces, runtime errors, or behavioral descriptions—and accurately classify the failure type. Misclassification of the issue is the most common cause of wasted diagnostic time; therefore, this triage step must be executed before any specialized debugging skill.

## Capabilities
*   **Failure Classification:** Reads input to determine if the issue is related to compilation, runtime crashes, network protocols, or remote environment issues.
*   **Intelligent Routing:** Automatically routes the request to one of several specialized sub-skills (e.g., `debug-patch-strategy`, `debug-runtime-behavior`) based on the identified failure type.
*   **Structured Output:** Provides a mandatory, highly structured response header detailing the Triage Result, Failure Type, and intended next step for clarity.

## Example Use Cases
*   **Compile Errors:** If you paste output containing `e: /path/to/File.kt:N:M: error:` or Gradle `FAILED` messages, this agent routes to the patching strategy skill.
*   **Crashes:** When provided with a logcat dump showing `FATAL EXCEPTION` or stack traces, it directs you to the runtime behavior analysis tool.
*   **Network Issues:** If the problem description points toward connectivity failures or protocol mismatches, it routes appropriately for network diagnosis.
*   **Remote Context:** If you mention that direct file access is unavailable, it correctly switches context to remote debugging protocols.