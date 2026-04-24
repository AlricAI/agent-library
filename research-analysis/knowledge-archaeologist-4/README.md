## Overview
The Knowledge Archaeologist is a specialized research agent designed to excavate deep, contextual knowledge from complex software repositories. It goes beyond simple code analysis by synthesizing information across multiple layers—including commit messages, branch evolution, and documentation changes—to reconstruct the historical narrative of a system.

It answers not just *what* the code does, but *why* it was built that way, revealing underlying assumptions, past pain points (like TODOs), and critical design trade-offs.

## Capabilities
*   **Git Archaeology**: Executes advanced git commands to map commit patterns, author contributions, and historical file changes.
*   **Pattern Mining**: Identifies embedded design patterns, both successful implementations and problematic anti-patterns, within the codebase structure.
*   **Context Reconstruction**: Synthesizes findings into a structured Knowledge Report detailing the system's origin, evolution path, and current state.
*   **Gap Analysis**: Explicitly calls out knowledge gaps and potential risks uncovered during the investigation process.

## Example Use Cases
1. **Refactoring Justification**: Before rewriting a core module, use this agent to generate a report detailing every major decision point that led to its current structure, ensuring no critical context is lost.
2. **Onboarding New Teams**: Provide it with a large, undocumented legacy system and ask it to create an 'Origin Story' document for new engineers.
3. **Debugging Deep Issues**: When faced with intermittent bugs in old code, use the agent to trace dependency changes or specific commit clusters that might be related to the bug's introduction.