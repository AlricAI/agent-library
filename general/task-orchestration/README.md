# Task Orchestration

> > Stop being the scheduler.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Task Orchestration

> Stop being the scheduler. Define the work, let the machine manage the queue.

## The Problem

You have 5 projects, each with a session. You open each one, paste "continue with next priorities", wait, switch, repeat. You're acting as a human cron job.

## The Pattern

Separate **planning** from **execution**:

1. **Plan once** — Analyze all projects, identify highest-value work, create a prioritized backlog
2. **Dispatch automatically** — A background process picks the next task, creates a session, sends the prompt
3. **Monitor completion** — When a session goes idle with all tasks done, mark complete and dispatch next
4. **Chain work** — Sequential tasks promote automatically when predecessors complete

### Task Lifecycle

```
backlog → ready → in_progress → done
                       ↓
                    blocked
```

- **backlog**: Planned but waiting (dependencies, sequencing)
- **ready**: Can be dispatched immediately
- **in_progress**: Assigned to a session, agent is working
- **done**: Work complete, verified
- **blocked**: Something went wrong, needs human attention

### Task Schema (Tool-Agnostic)

```json
{
  "id": "unique-id",
  "title": "Short description",
  "description": "Detailed instructions for the agent",
  "directory": "/path/to/project",
  "priority": "critical | high | medium | low",
  "status": "backlog | ready | in_progress | done | blocked",
  "tags": ["security", "api", "frontend"],
  "dependsOn": ["other-task-id"],
  "createdAt": 1710000000000,
  "updatedAt": 1710000000000
}
```

### Good Task Descriptions

**Bad**: "Fix the auth bug"

**Good**:
```
Fix the session timeout race condition in auth/middleware.ts.

The bug: when two requests arrive within 50ms of session expiry,
both pass the `isValid()` check but the first one triggers a refresh
that invalidates the second.

Fix: add a mutex around the refresh logic, or use optimistic locking
on the session version field.

Test: the existing test in auth/middleware.tes

*[truncated — see source for full prompt]*