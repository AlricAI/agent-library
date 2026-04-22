# Session Setup

> ## Quick Start

To create a new session, just set the `SESSION_NAME` environment variable when running `start.sh`:

```bash
SESSION_NAME=tales_of_wond

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Session Setup

## Quick Start

To create a new session, just set the `SESSION_NAME` environment variable when running `start.sh`:

```bash
SESSION_NAME=tales_of_wonder ./start.sh
```

If the session doesn't exist, you'll be guided through an interactive setup wizard!

## How It Works

### 1. Automatic Detection
When you run `start.sh` with a new session name, it checks if `data/sessions/<session_name>` exists.

### 2. Setup Wizard
If the session doesn't exist (and isn't `dev_session`), the setup wizard launches automatically:

```
🏰 MechaWiki Session Setup: tales_of_wonder
======================================================================

Let's configure your new session!

This wizard will help you set up:
  • Session directory structure
  • Wikicontent branch configuration
  • Initial session settings
```

### 3. Configuration Questions

The wizard asks:

1. **Wikicontent Branch**: Which branch should this session track?
   - Auto-detects your current branch as the default
   - Shows all available branches
   - You can select from the list or type a custom branch name

2. **Description** (optional): A human-readable description of this session

3. **Confirmation**: Review and confirm before creating

### 4. Session Created!

The wizard creates:
```
data/sessions/tales_of_wonder/
├── config.yaml      # Session config with branch info
├── agents.json      # Empty agents list (ready for agents!)
└── logs/            # Directory for agent logs
```

## Examples

### Development Session (auto-cleaned)
```bash
# Default - gets wiped on every start
./start.sh
```

### Persistent Story Session
```bash
# Create a new session for your story project
SESSION_NAME=tales_of_wonder ./start.sh

# On first run, wizard asks questions
# On subsequent runs, just loads the session
SESSION_NAME=tales_of_wonder ./start.sh
```

### Multiple Sessions
```bash
# Fantasy story session
SESSION_NAME=dragon_quest ./start.sh

# Horror story session
SESSION_NAME=haunted_manor ./start.sh

# 

*[truncated — see source for full prompt]*