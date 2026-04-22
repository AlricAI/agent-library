# Reference

> Complete documentation of all tools, parameters, and automated behavior.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# pi-teams Tool Reference

Complete documentation of all tools, parameters, and automated behavior.

---

## Table of Contents

- [Team Management](#team-management)
- [Teammates](#teammates)
- [Task Management](#task-management)
- [Messaging](#messaging)
- [Task Planning & Approval](#task-planning--approval)
- [Automated Behavior](#automated-behavior)
- [Task Statuses](#task-statuses)
- [Configuration & Data](#configuration--data)

---

## Team Management

### team_create

Start a new team with optional default model.

**Parameters**:
- `team_name` (required): Name for the team
- `description` (optional): Team description
- `default_model` (optional): Default AI model for all teammates (e.g., `gpt-4o`, `haiku`, `glm-4.7`)

**Examples**:
```javascript
team_create({ team_name: "my-team" })
team_create({ team_name: "research", default_model: "gpt-4o" })
```

---

### team_delete

Delete a team and all its data (configuration, tasks, messages).

**Parameters**:
- `team_name` (required): Name of the team to delete

**Example**:
```javascript
team_delete({ team_name: "my-team" })
```

---

### read_config

Get details about the team and its members.

**Parameters**:
- `team_name` (required): Name of the team

**Returns**: Team configuration including:
- Team name and description
- Default model
- List of members with their models and thinking levels
- Creation timestamp

**Example**:
```javascript
read_config({ team_name: "my-team" })
```

---

## Teammates

### spawn_teammate

Launch a new agent into a terminal pane with a role and instructions.

**Parameters**:
- `team_name` (required): Name of the team
- `name` (required): Friendly name for the teammate (e.g., "security-bot")
- `prompt` (required): Instructions for the teammate's role and initial task
- `cwd` (required): Working directory for the teammate
- `model` (optional): AI model for this teammate (overrides team default)
- `thinking` (optional): Thinking level (`off`, `minimal`, `low`, `medium`, `high`, `xhigh`

*[truncated — see source for full prompt]*