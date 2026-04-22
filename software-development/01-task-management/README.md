# 01 Task Management

> description: globs: alwaysApply: true

## System Prompt
---
description: 
globs: 
alwaysApply: true
---
<mcp-tool-availability-check>
If TodoRead/TodoWrite tools are unavailable, IGNORE ALL TODO RULES and proceed normally.
These guidance rules do NOT apply
Do NOT attempt to run any other commands or tools.
</mcp-tool-availability-check>

<tool-reference>
TodoRead: No parameters, returns current todos
TodoWrite: Takes `todos` array, replaces entire list

Todo Structure:
{
  "id": "unique-identifier",
  "content": "specific task description", 
  "status": "pending|in_progress|completed",
  "priority": "high|medium|low"
}

Visual Display Format:
Display complete todo list after every operation:
Current todos:
✅ Research existing patterns (completed)
🔄 Implement login form (in_progress)  
⏳ Add validation (pending)
⏳ Write tests (pending)

Icons: ✅ = completed, 🔄 = in_progress, ⏳ = pending
</tool-reference>

<state-management-rules>
1. Only ONE task "in_progress" at any time
2. Update status in real-time (never batch)
3. Mark completed IMMEDIATELY after finishing
4. Never mark completed if: tests failing, partial implementation, unresolved errors
5. For blockers: keep as "in_progress", create new task describing blocker
</state-management-rules>

<task-breakdown-examples>
"Add user authentication":
1. Research existing auth patterns in codebase
2. Design database schema for users/sessions
3. Implement user model and migrations
4. Create registration endpoint
5. Create login endpoint
6. Add JWT token generation
7. Implement auth middleware
8. Write unit tests for auth flow
9. Add integration tests
10. Update API documentation

"Fix performance issues":
1. Profile current performance bottlenecks
2. Analyze database query patterns
3. Implement query optimizations
4. Add caching layer
5. Optimize frontend bundle size
6. Run performance benchmarks
7. Document performance improvements
</task-breakdown-examples>

<critical-anti-patterns>
NEVER explore/research before creating todos:
❌ "Let me first understand the codebase..." → s

*[truncated — see source for full prompt]*