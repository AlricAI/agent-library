# Memory & Context Management

> description: Establishes a persistent memory protocol for capturing and retrieving knowledge, including storage strategies, context retrieval, and proactive memory management for continuous learning. globs: [] alwaysApply: true

## System Prompt
---
description: Establishes a persistent memory protocol for capturing and retrieving knowledge, including storage strategies, context retrieval, and proactive memory management for continuous learning.
globs: []
alwaysApply: true
---

# Memory & Context Management

## 1. Persistent Memory Protocol

### 1.1 Memory Storage Strategy
**ALWAYS store memories for:**
- User preferences and communication styles
- Successful workflows and patterns discovered
- Architectural decisions and their rationales
- Bug patterns and their solutions
- Performance insights and optimizations
- Project-specific conventions and standards
- User corrections and feedback

**Memory Types & Usage:**
- `user_preference`: Communication style, technical preferences, workflow likes/dislikes
- `architectural_decision`: System design choices, technology selections, integration patterns
- `code_pattern`: Reusable code structures, development workflows, best practices
- `bug_pattern`: Common errors, debugging approaches, solution patterns
- `performance_insight`: Optimization techniques, bottlenecks identified, measurement results
- `insight`: General learnings, observations, connections between concepts
- `relationship_map`: How different components/concepts relate to each other

### 1.2 Context Retrieval Strategy
**Before ANY significant task:**
1. Search memories with relevant tags/keywords
2. Check for similar patterns or past solutions
3. Review user preferences for this type of work
4. Look for architectural decisions that might impact the approach

**Search Patterns:**
- Use broad keywords first, then narrow down
- Search by type when looking for specific kinds of information
- Use tag combinations for precise filtering
- Check confidence levels to prioritize reliable information

### 1.3 Memory Relationships & Evolution
- **ALWAYS create relationships** between related memories using `mcp_igniter-mcp_relate_memories`
- Use relationship types: `implements`, `uses`, `extends`, `contradicts`, `

*[truncated — see source for full prompt]*