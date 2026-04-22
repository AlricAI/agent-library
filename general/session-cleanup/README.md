# SESSION CLEANUP

> ## Default: dev_session is EPHEMERAL

The `dev_session` is **completely wiped on every start** by design!

### What Gets Deleted

When you run `./star

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Session Cleanup Behavior 🗑️

## Default: dev_session is EPHEMERAL

The `dev_session` is **completely wiped on every start** by design!

### What Gets Deleted

When you run `./start.sh`, if `SESSION_NAME=dev_session` (the default):

```
data/sessions/dev_session/
├── config.yaml          ❌ DELETED
├── agents.json          ❌ DELETED
└── logs/
    ├── agent_*.jsonl    ❌ DELETED
    └── ...
```

### Why?

- **Clean slate every time** - No stale state between dev iterations
- **Predictable behavior** - You always know what you're starting with
- **Fresh agents** - No leftover logs or configurations

### Warning Display

When starting with `dev_session`, you'll see:

```
⚠️  ═══════════════════════════════════════════════════════════
⚠️  WARNING: Cleaning dev_session - ALL DATA WILL BE DELETED!
⚠️  ═══════════════════════════════════════════════════════════
⚠️  
⚠️  Deleting: data/sessions/dev_session/
⚠️  This includes:
⚠️    - All agent configurations
⚠️    - All agent logs
⚠️    - Session config
⚠️  
⚠️  💡 To preserve state between runs, use a different session:
⚠️     SESSION_NAME=my_session ./start.sh
⚠️  ═══════════════════════════════════════════════════════════
```

---

## Persistent Sessions

To keep data between runs, use a **named session**:

```bash
SESSION_NAME=production ./start.sh
```

or

```bash
SESSION_NAME=my_story ./start.sh
```

### Persistent Session Behavior

Named sessions (anything except `dev_session`):
- ✅ **Preserved** - Data survives restarts
- ✅ **Resumable** - Agents continue from where they left off
- ✅ **Historical** - All logs are kept

---

## Examples

### Development (ephemeral)
```bash
# Default - clean slate every time
./start.sh

# or explicitly
SESSION_NAME=dev_session ./start.sh
```

### Production (persistent)
```bash
SESSION_NAME=production ./start.sh
```

### Story Projects (persistent)
```bash
SESSION_NAME=tales_of_wonder ./start.sh
SESSION_NAME=dracula_analysis ./start.sh
SESSION_NAME=my_rpg_campaign ./start.sh
```

---


*[truncated — see source for full prompt]*