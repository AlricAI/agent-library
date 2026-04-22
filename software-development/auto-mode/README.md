# AUTO MODE

> Auto mode enables autonomous agentic loops with Claude Code or GitHub Copilot CLI, allowing AI to work through multi-turn workflows with minimal human intervention.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Auto Mode Documentation

Auto mode enables autonomous agentic loops with Claude Code or GitHub Copilot CLI, allowing AI to work through multi-turn workflows with minimal human intervention.

## Overview

Auto mode orchestrates an intelligent loop that:

1. Clarifies objectives with measurable evaluation criteria
2. Creates detailed execution plans identifying parallel opportunities
3. Executes plans autonomously through multiple turns
4. Evaluates progress after each turn
5. Continues until objective achieved or max turns reached
6. Provides comprehensive summary of work completed

## Usage

### With Claude Code

```bash
# Basic auto mode
amplihack claude --auto -- -p "implement user authentication"

# With custom max turns
amplihack claude --auto --max-turns 20 -- -p "refactor the API module"

# With interactive UI (requires Rich library)
amplihack claude --auto --ui -- -p "implement user authentication"
```

The legacy `amplihack launch` alias also supports `--auto`, but user-facing
examples should prefer `amplihack claude`.

### Interactive UI Mode (`--ui`)

Auto mode supports an optional interactive terminal UI that displays real-time progress with:

- Session title and details (turn counter, elapsed time, cost tracking)
- Todo list with status indicators
- Streaming log output
- Interactive controls (pause, resume, exit)

**Installing UI Dependencies:**

The UI feature requires the Rich library. Install it with:

```bash
# Install with optional UI dependencies
pip install 'amplihack[ui]'

# Or install Rich directly
pip install 'rich>=13.0.0'
```

**Usage:**

```bash
# Enable interactive UI
amplihack claude --auto --ui -- -p "implement user authentication"
```

**What happens if Rich is not installed:**

If you use the `--ui` flag without Rich installed, auto mode will display a helpful error message and continue in non-UI mode:

```
⚠️  WARNING: --ui flag requires Rich library
   Error: No module named 'rich'

   To enable TUI mode, install Rich:
     pip ins

*[truncated — see source for full prompt]*