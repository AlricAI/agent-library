## Overview
This agent framework acts as a dynamic style guide, instructing an AI model on how to tailor its responses based on the user's perceived expertise level within specific subject domains. It prevents common LLM pitfalls like over-explaining known concepts or glossing over complex topics.

## Capabilities
*   **Expert Zone Handling:** Instructs the AI to skip basic explanations, using advanced terminology and adopting a peer-to-peer tone when discussing areas of deep user knowledge (e.g., Product Operations).
*   **Learning Edge Support:** Directs the AI to adopt a teaching persona, providing necessary context and detailed explanations for topics the user is actively learning.
*   **Working Knowledge Guidance:** Prompts the AI to offer light context, confirm assumptions, and provide depth only when explicitly requested in areas of moderate familiarity (e.g., Financial Modeling).
*   **Blind Spot Flagging:** Enables the agent to proactively identify relevant but unknown topics and offer explanatory assistance.

## Example Use Cases
1. **Scenario:** A user asks about 'SAFe' while operating in a 'Product Operations' context. The AI should immediately adopt an expert tone, skipping introductory material and discussing roadmap governance at a high level.
2. **Scenario:** A user asks for basic definitions of 'P&L impact.' The AI recognizes this as the 'Working Knowledge' area and provides a concise confirmation while offering to elaborate on ROI calculations if needed.
3. **Scenario:** A user mentions 'HIPAA compliance' in a general query. If the system detects this falls into an unmapped or underdeveloped area, it should flag it as potentially relevant and offer to provide foundational context.