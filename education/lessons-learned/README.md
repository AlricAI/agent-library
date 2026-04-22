# Lessons Learned

> This document captures hard-won operational knowledge from building the first version of Machinator.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Lessons Learned: Machinator Orchestrator v1

This document captures hard-won operational knowledge from building the first version of Machinator. These lessons should inform the architecture of v2.

## Gemini Invocation

### Environment Setup

Gemini CLI uses several environment variables to find its configuration:

```bash
# BOTH must be set to the account directory for proper isolation
HOME=/path/to/account/dir
GEMINI_CLI_HOME=/path/to/account/dir

# Bypass macOS Keychain (which is shared across all processes)
GEMINI_FORCE_FILE_STORAGE=true
```

**Why both HOME and GEMINI_CLI_HOME?**

- `HOME` is where Gemini looks for `.gemini/` by default
- `GEMINI_CLI_HOME` is an explicit override
- Some code paths check one, some check the other
- Setting both ensures consistent behavior

### Working Directory

```bash
# Run from the agent's worktree, NOT the main repo
geminiCmd.Dir = "/path/to/agents/1/"
```

The `--sandbox` flag restricts file access to the current directory tree. If you run from the wrong directory, gemini can't access the files it needs.

### Command Flags

```bash
gemini \
  --yolo \                    # Skip confirmation prompts
  --sandbox \                 # Restrict file access to cwd
  --model gemini-3-flash \    # Or gemini-3-pro for complex tasks
  --output-format stream-json \ # Get parseable ACP events
  "Your directive here"
```

### Directive Delivery (Future Improvement)

Instead of passing a massive inline directive, write to a file:

```bash
# Write directive to agent's worktree
cat > agents/1/.machinator/directive.md << 'EOF'
# Task Assignment
Agent: Agent-1
Task: TASK-123
...
EOF

# Simple prompt that points to the file
gemini --yolo --sandbox "Read .machinator/directive.md for your instructions."
```

Benefits:

- No escaping nightmares with quotes/newlines
- Debuggable (cat the file to see what agent was told)
- Agent can reread mid-task if it loses context
- Avoids OS argument length limits

---

## Beads Database Management

### The 

*[truncated — see source for full prompt]*