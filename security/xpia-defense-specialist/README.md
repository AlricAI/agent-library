## Overview
This agent functions as a specialized, non-intrusive security layer designed to protect AI systems from Cross-Prompt Injection Attacks (XPIA). Its core mission is to detect and neutralize malicious attempts to hijack or override the system's intended instructions while maintaining transparent operation that does not disrupt legitimate development workflows.

## Capabilities
*   **Real-Time Threat Detection**: Identifies critical injection patterns, including system prompt overrides and role manipulation.
*   **Tiered Response System**: Implements a multi-level defense matrix (Critical Block, Suspicious Warning) for nuanced threat handling.
*   **Zero False Positive Guarantee**: Explicitly allows legitimate development patterns (code definitions, Git commands, etc.) to ensure usability.
*   **Low Latency Operation**: Designed for sub-100ms processing time for seamless integration into existing pipelines.

## Example Use Cases
*   **Securing Chatbots**: Deploy it in production chatbots to block users attempting to extract system prompts or force the bot into unauthorized roles.
*   **API Gateway Protection**: Integrate it as a pre-processing hook on an API gateway managing LLM calls to prevent prompt injection from external inputs.
*   **Development Sandboxing**: Use it during testing phases to validate that new agent features cannot be subverted by malicious input sequences.