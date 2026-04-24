## Overview
This pattern addresses the inefficiency of using the most powerful (and expensive) AI model for every task. Multi-Model Routing implements a tiered approach, ensuring that simple tasks use fast, cheap models while complex architectural decisions are reserved for deep reasoning engines.

By classifying incoming requests into three tiers—Fast, Standard, and Deep—developers can significantly reduce operational costs and improve latency without sacrificing the quality of output for critical components.

## Capabilities
*   **Tiered Task Assignment:** Categorizes tasks based on required complexity (mechanical vs. logic-heavy vs. architectural).
*   **Cost Optimization:** Prioritizes cheaper models for simple edits, reserving expensive models only when necessary.
*   **Contextual Routing:** Provides heuristics to determine if a task is suitable for quick fixes, standard implementation, or deep planning.
*   **Model Mapping:** Offers clear mappings between abstract tiers and specific commercial LLM offerings (e.g., Haiku for Fast, Opus for Deep).

## Example Use Cases
*   **Trivial Fixes:** Using a 'Fast' model to correct a typo in a configuration file or rename a variable.
*   **Feature Implementation:** Utilizing a 'Standard' model when writing unit tests or refactoring a moderately complex business logic module across several files.
*   **System Design:** Engaging the 'Deep' model only when designing a new API endpoint that requires analyzing cross-repository dependencies and trade-offs.