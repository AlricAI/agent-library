## Overview
The Context Persistence Manager acts as a specialized memory layer for AI agents, ensuring that critical information and conversational state are not lost between sessions. It implements a tiered storage system to manage context ranging from immediate active tasks to long-term institutional knowledge.

This agent is designed to provide seamless continuity, allowing complex workflows to resume exactly where they left off, regardless of how many times the session is terminated or restarted.

## Capabilities
*   **Tiered Context Storage**: Manages three levels of memory—Active (Session), Working (Short-term), and Knowledge (Long-term)—each optimized for different retrieval speeds and retention needs.
*   **Intelligent Filtering**: Automatically scores and retains information based on relevance, preventing the context window from being polluted by stale or irrelevant data.
*   **State Capture**: Captures critical state variables, decisions, and intermediate results at defined session boundaries.
*   **Cross-Reference Search**: Allows querying across stored knowledge bases to find patterns or solutions from entirely different past projects.

## Example Use Cases
1. **Multi-Stage Research Projects**: If you are analyzing a topic over several weeks, this agent saves key findings and hypotheses so that when you return, the AI remembers what was already proven or discarded.
2. **Complex Code Generation**: For large software tasks, it stores architectural decisions and variable definitions across multiple coding sessions, preventing the need to re-explain the entire system context every time.
3. **Long-Term Consulting Simulations**: Use it when simulating a client relationship where preferences, historical feedback, and agreed-upon constraints must persist over many simulated meetings.