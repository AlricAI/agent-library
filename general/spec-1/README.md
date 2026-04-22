# SPEC

> Target specification for the Paperclip control plane.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Paperclip Specification

Target specification for the Paperclip control plane. Living document — updated incrementally during spec interviews.

---

## 1. Company Model [DRAFT]

A Company is a first-order object. One Paperclip instance runs multiple Companies. A Company does not have a standalone "goal" field — its direction is defined by its set of Initiatives (see Task Hierarchy Mapping).

### Fields (Draft)

| Field       | Type          | Notes                             |
| ----------- | ------------- | --------------------------------- |
| `id`        | uuid          | Primary key                       |
| `name`      | string        | Company name                      |
| `createdAt` | timestamp     |                                   |
| `updatedAt` | timestamp     |                                   |

### Board Governance [DRAFT]

Every Company has a **Board** that governs high-impact decisions. The Board is the human oversight layer.

**V1: Single human Board.** One human operator.

#### Board Approval Gates (V1)

- New Agent hires (creating new Agents)
- CEO's initial strategic breakdown (CEO proposes, Board approves before execution begins)
- [TBD: other governance-gated actions — goal changes, firing Agents?]

#### Board Powers (Always Available)

The Board has **unrestricted access** to the entire system at all times:

- **Set and modify Company budgets** — the Board sets top-level token/LLM cost budgets
- **Pause/resume any Agent** — stop an Agent's heartbeat immediately
- **Pause/resume any work item** — pause a task, project, subtask tree, milestone. Paused items are not picked up by Agents.
- **Full project management access** — create, edit, comment on, modify, delete, reassign any task/project/milestone through the UI
- **Override any Agent decision** — reassign tasks, change priorities, modify descriptions
- **Manually change any budget** at any level

The Board is not just an approval gate — it's a live control surface. The human can interv

*[truncated — see source for full prompt]*