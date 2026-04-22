# Claude Dispatch

> ## Goal

Translate standard agent team manifests into Claude Code-native instructions, enabling true parallel subagent spawning via the Agent tool, wo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claude Code Native Dispatch

## Goal

Translate standard agent team manifests into Claude Code-native instructions, enabling true parallel subagent spawning via the Agent tool, worktree isolation, and cloud scheduling.

## When to Use

| Scenario | Mode | Command |
|----------|------|---------|
| Orchestrating from Claude Code (local) | `native` | `--mode native` (default) |
| Orchestrating from non-Claude agent | `fallback` | `--mode fallback` |
| Scheduling for cloud/remote execution | `schedule` | `--mode schedule` or `--cloud` |

**Auto-detection:** If `CLAUDE_CODE` or `CLAUDE_SESSION_ID` env vars are set, `dispatch_agent_team.py --claude` auto-pipes through the adapter. Override with `--no-claude`.

## Detection Logic

```
CLAUDE_CODE env var set?        → yes → native mode
CLAUDE_SESSION_ID env var set?  → yes → native mode
`claude` CLI in PATH?           → yes → native mode (weak signal)
None detected                   → fallback mode + warning
```

## Dispatch Modes

### Native Mode (default)

Outputs a JSON array of `agent_calls` for the Claude Code Agent tool:

```bash
python3 execution/claude_dispatch.py \
  --team documentation_team \
  --payload '{"changed_files": ["execution/foo.py"], "commit_msg": "feat: foo"}'
```

Each agent call includes:
- Complete prompt with directive content, payload, memory commands
- `isolation: "worktree"` for parallel teams
- `subagent_type: "general-purpose"`
- Cross-agent context commands (Qdrant stores for Gemma 4 visibility)

### Fallback Mode

Returns the standard manifest from `dispatch_agent_team.py` unchanged:

```bash
python3 execution/claude_dispatch.py --team qa_team \
  --payload '{"task": "run tests"}' --mode fallback
```

### Schedule Mode

Generates self-contained prompts for `/schedule` cloud dispatch:

```bash
python3 execution/claude_dispatch.py --team security_team \
  --payload '{"scan_type": "full"}' --mode schedule
```

Cloud prompts include `session_boot.py` setup since cloud tasks run in fresh clon

*[truncated — see source for full prompt]*