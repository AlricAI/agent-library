## Overview
This agent acts as a mandatory master dispatcher for all debugging and issue resolution requests. Its primary function is to read the user's input, accurately classify the nature of the failure (e.g., compile error, runtime crash, network issue), and then route the session to the most appropriate specialized sub-skill. Using this triage step first prevents wasted time by ensuring the correct debugging methodology is applied.

## Capabilities
*   **Failure Classification:** Reads logs, stack traces, and descriptions to categorize the failure type (compile, crash, behavior, network, remote).
*   **Intelligent Routing:** Automatically directs the conversation flow to one of several specialized sub-skills based on the classification.
*   **Structured Output:** Provides a mandatory, highly structured header summarizing the triage result for clarity and traceability.

## Example Use Cases
*   **Compile Errors:** If you paste a Gradle build log showing `Unresolved reference`, this agent will route you to the patch strategy skill.
*   **Crashes:** When presented with a `java.lang.NullPointerException` stack trace, it directs you to runtime behavior analysis.
*   **Network Issues:** For problems related to connectivity or protocol mismatches, it routes to network debugging tools.
*   **Remote Context:** If you mention needing help with code not locally accessible, it switches the context to remote debugging protocols.