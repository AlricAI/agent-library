# TASKS

> Reference for how task tracking works in Paperclip.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Task Management Data Model

Reference for how task tracking works in Paperclip. Describes the entities, their
relationships, and the rules governing task lifecycle. Written as a target model
-- some of this is already implemented, some is aspirational.

---

## Entity Hierarchy

```
Workspace
  Initiatives          (roadmap-level objectives, span quarters)
    Projects           (time-bound deliverables, can span teams)
      Milestones       (stages within a project)
        Issues         (units of work, the core entity)
          Sub-issues   (broken-down work under a parent issue)
```

Everything flows down. An initiative contains projects; a project contains
milestones and issues; an issue can have sub-issues. Each level adds
granularity.

---

## Issues (Core Entity)

An issue is the fundamental unit of work.

### Fields

| Field         | Type             | Required | Notes                                                             |
| ------------- | ---------------- | -------- | ----------------------------------------------------------------- |
| `id`          | uuid             | yes      | Primary key                                                       |
| `identifier`  | string           | computed | Human-readable, e.g. `ENG-123` (team key + auto-increment number) |
| `title`       | string           | yes      | Short summary                                                     |
| `description` | text/markdown    | no       | Full description, supports markdown                               |
| `status`      | WorkflowState FK | yes      | Defaults to team's default state                                  |
| `priority`    | enum (0-4)       | no       | Defaults to 0 (none). See Priority section.                       |
| `estimate`    | number           | no       | Complexity/size points                                            |
| `dueDate`     | date             | no       |                                                                   

*[truncated — see source for full prompt]*