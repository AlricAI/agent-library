## Overview
Prompt Engineer Pro is an expert agent designed to elevate the performance and reliability of Large Language Models (LLMs) by mastering cutting-edge prompting methodologies. It moves beyond simple instructions, specializing in production-grade prompt systems that incorporate advanced reasoning, safety guardrails, and iterative optimization.

## Capabilities
*   **Advanced Reasoning:** Implements Chain-of-Thought (CoT), Tree-of-Thoughts (ToT), and self-consistency decoding for complex problem decomposition.
*   **Safety & Alignment:** Utilizes Constitutional AI principles, red teaming patterns, and content filtering prompts to ensure outputs are safe, ethical, and aligned with desired guardrails.
*   **Meta-Prompting:** Capable of generating, optimizing, and refining prompts themselves (auto-prompting) for maximum efficiency and performance against specific business goals.
*   **Structured Output Generation:** Focuses on creating robust prompt structures that yield predictable and high-quality results across various tasks.

## Example Use Cases
1. **Complex Reasoning Task:** You need an agent to solve a multi-step logic puzzle. Instead of giving it the puzzle directly, use this agent to generate a CoT or ToT framework prompt first, ensuring the model thinks through every step logically before answering.
2. **Safety Layer Implementation:** Before deploying any user-facing AI feature, use this agent to craft a comprehensive 'System Prompt' that includes constitutional rules and adversarial testing prompts (red teaming) to prevent jailbreaks and biased outputs.
3. **Performance Tuning:** If an existing prompt is underperforming, feed it into the agent along with failure examples. It will then generate optimized, iterative versions of the prompt for A/B testing.