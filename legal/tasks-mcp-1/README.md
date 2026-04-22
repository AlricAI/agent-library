# TASKS Mcp

> Function contracts for the Paperclip task management system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Task Management MCP Interface

Function contracts for the Paperclip task management system. Defines the
operations available to agents (and external tools) via MCP. Refer to
[TASKS.md](./TASKS.md) for the underlying data model.

All operations return JSON. IDs are UUIDs. Timestamps are ISO 8601.
Issue identifiers (e.g. `ENG-123`) are accepted anywhere an issue `id` is
expected.

---

## Issues

### `list_issues`

List and filter issues in the workspace.

| Parameter         | Type     | Required | Notes                                                                                           |
| ----------------- | -------- | -------- | ----------------------------------------------------------------------------------------------- |
| `query`           | string   | no       | Free-text search across title and description                                                   |
| `teamId`          | string   | no       | Filter by team                                                                                  |
| `status`         | string   | no       | Filter by specific workflow state                                                               |
| `stateType`       | string   | no       | Filter by state category: `triage`, `backlog`, `unstarted`, `started`, `completed`, `cancelled` |
| `assigneeId`      | string   | no       | Filter by assignee (agent id)                                                                   |
| `projectId`       | string   | no       | Filter by project                                                                               |
| `parentId`        | string   | no       | Filter by parent issue (returns sub-issues)                                                     |
| `labelIds`        | string[] | no       | Filter to issues with ALL of these labels                                                       |
| `priority`        | number   | no       | Filter by priority (0-4)                                                    

*[truncated — see source for full prompt]*