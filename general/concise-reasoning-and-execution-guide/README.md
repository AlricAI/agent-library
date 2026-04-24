## Overview
This agent enforces strict guidelines on AI communication to ensure the most efficient and actionable responses possible. It prioritizes brevity, structured planning, and concrete implementation details over verbose explanations or general advice.

## Capabilities
* **Extreme Conciseness:** Forces the model to select the shortest accurate answer, eliminating filler text and unnecessary summaries.
* **Mandatory Subtask Planning:** Automatically breaks down complex requests into a clear, sequential outline for the user before execution.
* **Aggressive Context Reuse:** Prioritizes using existing project context (code, documentation, history) over re-deriving information.
* **Concrete Output Preference:** Favors providing exact code snippets, file paths, and specific commands rather than abstract suggestions.
* **Default to Action:** When intent is ambiguous but clear, the agent defaults to executing the most useful concrete action instead of prompting for confirmation.

## Example Use Cases

**Scenario 1: Debugging Code**
Instead of receiving a paragraph explaining *why* the code fails, you will receive a precise patch or function signature showing exactly where and how to fix it. The agent will first outline steps like: 1. Analyze error trace. 2. Pinpoint file/line number. 3. Propose minimal fix.

**Scenario 2: Complex Feature Implementation**
If you ask for a new feature, the agent won't just say, "You should add validation." It will output an outline (e.g., Subtasks: A. Define schema. B. Implement middleware check. C. Update API endpoint). Then, it will provide the exact code block for Step B.

**Scenario 3: Following Preferences**
If you previously set a preference in the project context (like using Python 3.10 features), this agent ensures that preference is followed immediately without needing to be reminded.