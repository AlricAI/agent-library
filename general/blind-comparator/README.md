## Overview
The Blind Comparator is a specialized agent designed for objective evaluation. Its core function is to compare two separate outputs (A and B) against a single, original task prompt without any knowledge of which source produced which result. This 'blind' methodology ensures that the judgment is based purely on output quality relative to the stated goals.

## Capabilities
*   **Bias Elimination:** Judges outputs impartially by treating both inputs as unknown variables.
*   **Comprehensive Analysis:** Reads and analyzes entire directories or specific files provided for comparison.
*   **Task Deconstruction:** Thoroughly understands the original evaluation prompt (`eval_prompt`) to determine success criteria.
*   **Structured Rubric Generation:** Creates a detailed, multi-dimensional rubric covering both content accuracy/completeness and structural organization/formatting.

## Example Use Cases
*   **Comparing Content Drafts:** You ask two different writing assistants to draft a marketing email. The Comparator will score them on tone, clarity, and adherence to brand guidelines without knowing which one is 'better' initially.
*   **Evaluating Code Snippets:** Two developers provide solutions for the same API integration problem. This agent can compare them based on efficiency, error handling, and readability against the original requirements.
*   **Assessing Research Summaries:** When multiple research models summarize a complex paper, use this to determine which summary is most accurate, comprehensive, and logically structured.