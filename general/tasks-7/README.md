# TASKS

> Tasks are the atomic unit of work in Pixelpit.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pixelpit Task System

Tasks are the atomic unit of work in Pixelpit. They're how agents coordinate without getting lost.

**Why this matters for Haiku**: Small models stay focused with clear, specific instructions. One task = one thing. No ambiguity.

## Task Structure

Every task in `pixelpit_state` (type='task') has this shape:

```json
{
  "type": "task",
  "key": "task_XXX",
  "data": {
    "description": "What needs to be done (specific, actionable)",
    "assignee": "m1 | m2 | m3 | m4 | m5 | mobile_tester | desktop_tester | mayor",
    "status": "pending | in_progress | blocked | done | killed",
    "created_by": "who created this task",
    "game": "g1 | g2 | etc (if game-related)",
    "acceptance": "How to know this is DONE (specific criteria)",
    "blockers": ["list of blocking issues if status=blocked"],
    "notes": ["any updates or context"],
    "created_at": "ISO timestamp",
    "completed_at": "ISO timestamp (when done)"
  }
}
```

## Task Lifecycle

```
PENDING → IN_PROGRESS → DONE
              ↓
           BLOCKED → (unblocked) → IN_PROGRESS
              ↓
            KILLED (if abandoned)
```

## Rules for Agents

### When You Start Work

1. **Claim the task** — Set status to `in_progress`
2. **Read acceptance criteria** — Know what "done" means before you start
3. **Check blockers** — Don't start blocked tasks

```sql
UPDATE pixelpit_state
SET data = data || '{"status": "in_progress"}'::jsonb
WHERE type = 'task' AND key = 'task_XXX';
```

### When You Finish

1. **Verify acceptance criteria** — Did you actually meet them?
2. **Mark done** — Set status to `done`, add `completed_at`
3. **Create follow-up tasks** — If your work spawns new work, make tasks for it

```sql
UPDATE pixelpit_state
SET data = data || '{"status": "done", "completed_at": "2025-01-24T..."}'::jsonb
WHERE type = 'task' AND key = 'task_XXX';
```

### When You're Blocked

1. **Mark blocked** — Set status to `blocked`
2. **Explain why** — Add to `blockers` array
3. **Create u

*[truncated — see source for full prompt]*