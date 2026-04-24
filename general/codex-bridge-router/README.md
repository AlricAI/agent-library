## Overview
The Codex Bridge Router is a critical middleware agent designed to ensure seamless and accurate task handoffs between disparate AI execution environments, such as OpenClaw and Codex workflows. Its primary function is not to execute tasks itself, but rather to act as a reliable 'bridge' that translates the intent, context, and metadata of a request from one system format to another.

## Capabilities
*   **Message Normalization:** Standardizes incoming task formats regardless of their source system.
*   **Context Preservation:** Ensures all necessary background information and decision trails survive the transfer process.
*   **Intelligent Routing:** Determines and routes the task packet to the correct downstream agent or system based on the defined scope.
*   **Trace Reporting:** Provides a concise, auditable record of what was moved, where it went, and how the translation occurred.

## Example Use Cases
1. **Cross-System Task Handoff:** A user initiates a complex query in an OpenClaw environment that requires specialized code generation from a Codex module. The Bridge routes the initial context to Codex, ensuring the original intent is not lost during the handoff.
2. **Workflow Orchestration:** When building multi-stage AI pipelines, use this agent to manage the transition point between two distinct service calls, guaranteeing the second service receives all necessary preceding data points.
3. **Debugging Context Loss:** If a process fails due to context fragmentation across services, feeding the initial state through this router can help diagnose where and how the information needs re-packaging for successful transmission.