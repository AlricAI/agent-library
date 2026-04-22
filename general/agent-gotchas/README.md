# Agent Gotchas

> > AI agents are powerful but predictably unreliable.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Agent Gotchas

> AI agents are powerful but predictably unreliable. Know their failure modes.

## The Problem

AI coding agents fail in consistent, predictable ways. They fabricate npm packages that don't exist. They catch errors and continue silently. They add features you never asked for. They lose context mid-session and forget what they were doing.

These aren't bugs—they're fundamental characteristics of LLM-based agents. You can't fix them, but you can work around them.

The insight: AI agents are reliable tools with unreliable execution. Build guardrails, verify outputs, and design workflows that assume failure.

## The Pattern

### 1. Atomic Edits for Multi-File Changes

**Problem:** AI tools like Edit or Write run individually. If you make 5 file changes, there are 5 separate tool calls. Between tool calls, hooks can run, other sessions can interfere, or the agent can lose context.

**Example failure:**
```
Agent: "I'll update 3 files for the auth feature"
[Edit file1.ts] ✓
[PostToolUse hook runs, reformats file1.ts]
[Edit file2.ts] ✓
[Another session force-pushes, rebases branch]
[Edit file3.ts] ✗ Fails, branch state changed

Result: Partial implementation, inconsistent state
```

**Solution: Single-transaction pattern**

Use a shell script to make all changes atomically:

```bash
python3 << 'EOF'
import json

# Read all files
with open('file1.ts', 'r') as f:
    file1 = f.read()
with open('file2.ts', 'r') as f:
    file2 = f.read()
with open('file3.ts', 'r') as f:
    file3 = f.read()

# Make all changes
file1 = file1.replace('old1', 'new1')
file2 = file2.replace('old2', 'new2')
file3 = file3.replace('old3', 'new3')

# Write all files
with open('file1.ts', 'w') as f:
    f.write(file1)
with open('file2.ts', 'w') as f:
    f.write(file2)
with open('file3.ts', 'w') as f:
    f.write(file3)
EOF

# Atomic commit
git add file1.ts file2.ts file3.ts
git commit -m "feat: implement auth feature"
```

**Why this works:**
- All file changes happen in one tool c

*[truncated — see source for full prompt]*