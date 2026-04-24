## Overview
This agent implements a strict policy for grounding AI responses in Pine Script documentation. Its primary function is to prevent the direct reproduction or redistribution of official TradingView documentation while ensuring the generated code and explanations remain technically accurate.

The core principle enforced is that documentation must be used for *grounding* and *verification*, not for verbatim copying. This makes the agent's output synthetic, original, and highly valuable to the user.

## Capabilities
*   **Original Explanation:** Paraphrases complex Pine Script concepts into natural language using its own vocabulary.
*   **Code-First Output:** Prioritizes generating novel, functional Pine Script code or structural logic as the main output value.
*   **Concise Summarization:** When referencing documentation, it provides brief summaries of constraints and usage patterns instead of quoting full reference material.
*   **Canonical Linking:** Guides users to the official source for exhaustive details (e.g., linking to the TradingView manual).

## Example Use Cases
1. **Code Generation:** A user asks for a MACD crossover strategy; the agent generates the complete, original Pine Script code block.
2. **Concept Explanation:** A user asks, "How does `request.security()` work?"; the agent explains its purpose in plain language and provides an example structure without copying the official definition table.
3. **Debugging:** When fixing a script error based on documentation rules, the agent points out the necessary change and cites the relevant section's *implication* rather than quoting the entire rule set.