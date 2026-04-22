# Configuration

> All Workshop configuration is set through `configure/1` or individual
functions. Configuration is stored in `:persistent_term` for zero-cost reads.

#

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration Reference

All Workshop configuration is set through `configure/1` or individual
functions. Configuration is stored in `:persistent_term` for zero-cost reads.

## configure/1

```elixir
configure(
  backend: AgentWorkshop.Backends.Claude,
  backend_config: ClaudeWrapper.Config.new(working_dir: "."),
  model: "sonnet",
  permission_mode: :bypass_permissions,
  context: "Elixir project. Run mix test before committing.",
  max_cost_usd: 10.00,
  mcp: [port: 4222],
  dashboard: true,
  persistence: true,
  git_context: true
)
```

### Required options

| Option | Description |
|--------|-------------|
| `:backend` | Backend module (e.g., `AgentWorkshop.Backends.Claude`) |
| `:backend_config` | Backend-specific configuration struct |

### Agent defaults

These apply to all agents unless overridden per-agent:

| Option | Default | Description |
|--------|---------|-------------|
| `:model` | (none) | LLM model name (e.g., `"sonnet"`, `"opus"`, `"haiku"`) |
| `:permission_mode` | `:auto` | `:default`, `:accept_edits`, `:bypass_permissions`, `:dont_ask`, `:plan`, `:auto` |
| `:context` | (none) | System prompt prepended to all agents |
| `:max_cost_usd` | (none) | Global cost budget across all agents |

### Feature toggles

| Option | Default | Description |
|--------|---------|-------------|
| `:mcp` | (none) | Start MCP server. Pass `[port: 4222]` or just `true` for default port. |
| `:dashboard` | `false` | Start LiveView dashboard on port 4223 |
| `:persistence` | `false` | Enable disk persistence. Pass `true` for `.agent_workshop/` or a path string. |
| `:git_context` | `false` | Inject git branch, status, and recent commits into agent prompts |

## Agent options

Options passed to `agent/3` override global defaults:

```elixir
agent(:impl, "You write clean, well-tested code.",
  model: "sonnet",
  max_turns: 15,
  timeout: :timer.minutes(5),
  max_cost_usd: 2.00,
  allowed_tools: ["Read", "Edit", "Write", "Bash"],
  skill: :pair,
  workshop_tools: true

*[truncated — see source for full prompt]*