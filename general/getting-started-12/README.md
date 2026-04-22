# Getting Started

> AgentWorkshop is a multi-agent orchestration library for Elixir.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started

AgentWorkshop is a multi-agent orchestration library for Elixir. You create
LLM agents, give them roles, and coordinate their work -- all from IEx.

## Prerequisites

AgentWorkshop runs CLI-based LLM tools on your behalf. You need at least one
installed and authenticated:

- **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** -- `claude`
  CLI, authenticated via `claude login`. This is the recommended backend.
- **[OpenAI Codex](https://github.com/openai/codex)** -- `codex` CLI, with
  `OPENAI_API_KEY` set. Alternative backend.

Agents run these CLIs as your user, with your credentials and permissions.
They can read and write files, run shell commands, and make git commits --
just like you would from the terminal. Use `permission_mode` and
`allowed_tools` to control what agents can do.

For source control features (git context injection, worktrees for parallel
agents, GitHub integration):

- **git** -- any recent version
- **[gh](https://cli.github.com/)** -- GitHub CLI, authenticated via
  `gh auth login`. Needed for the GitHub integration skill.

## Installation

Add `agent_workshop` and a backend to your `mix.exs`:

```elixir
def deps do
  [
    {:agent_workshop, "~> 0.3"},
    {:claude_wrapper, "~> 0.4"}  # Claude Code CLI backend
  ]
end
```

Optional dependencies unlock additional features:

```elixir
# MCP server (expose Workshop as tools for other agents)
{:anubis_mcp, "~> 1.0"},
{:bandit, "~> 1.0"},
{:plug, "~> 1.16"},

# LiveView dashboard (real-time web UI)
{:phoenix, "~> 1.7"},
{:phoenix_live_view, "~> 1.0"},
{:phoenix_html, "~> 4.0"},

# Git context injection
{:git, "~> 0.2"},

# Alternative backend
{:codex_wrapper, "~> 0.2"}  # OpenAI Codex CLI
```

## First session

Start IEx in your project:

```
$ iex -S mix
```

Import the Workshop API and configure your backend:

```elixir
import AgentWorkshop.Workshop

configure(
  backend: AgentWorkshop.Backends.Claude,
  backend_config: ClaudeWrapper.Config.new(working_dir: ".")

*[truncated — see source for full prompt]*