# TOOLS

> Canonical commands. Copy-paste with variables replaced.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tools — DirtSync Simulator Specialist

Canonical commands. Copy-paste with variables replaced.

## Required env (set by orchestrator at spawn)

- `FORGE_AGENT_ID` — my agent UUID
- `FORGE_RUN_ID` — this run's UUID
- `FORGE_API_URL` — `http://localhost:3200` (Mini agent API)
- `CLAUDE_CODE_OAUTH_TOKEN` — my Claude Max auth
- `SUPABASE_URL` — `https://ncwxeeqvujgyiggkviqq.supabase.co`
- `SUPABASE_SERVICE_ROLE_KEY` — privileged writes

## Constants

```
SIM=1C53DE6B-2574-43FF-BF29-C1C5ACF5A526   # iPhone 17, iOS 26.4
BUNDLE=app.dirtsync.DirtSync
REPO=/Users/dirtsyncmini/DirtSync
PROJ=/Users/dirtsyncmini/DirtSync/DirtSync    # where .xcodeproj lives
BUILD=/tmp/dirtsync-build
```

## Agent API (for comments + inbox)

**Check my inbox:**
```bash
curl -s "$FORGE_API_URL/api/agent/me/inbox" -H "X-Forge-Agent-Id: $FORGE_AGENT_ID"
```

**Issue context:**
```bash
curl -s "$FORGE_API_URL/api/agent/issues/$ISSUE_ID/context" -H "X-Forge-Agent-Id: $FORGE_AGENT_ID"
```

**Post a comment (standalone — shipped via FORGE-271):**
```bash
curl -sS -X POST "$FORGE_API_URL/api/agent/issues/$ISSUE_ID/comments" \
  -H "X-Forge-Agent-Id: $FORGE_AGENT_ID" \
  -H "X-Forge-Run-Id: $FORGE_RUN_ID" \
  -H "Content-Type: application/json" \
  -d "{\"body\": \"[START] <plan text>\"}"
```

**Update issue status + proof:**
```bash
curl -sS -X PATCH "$FORGE_API_URL/api/agent/issues/$ISSUE_ID" \
  -H "X-Forge-Agent-Id: $FORGE_AGENT_ID" \
  -H "X-Forge-Run-Id: $FORGE_RUN_ID" \
  -H "Content-Type: application/json" \
  -d '{"status": "in_review", "proof_summary": "all 5 assertions pass, evidence bundle at <url>"}'
```

## Sim lifecycle

**Boot + clean:**
```bash
xcrun simctl boot $SIM 2>/dev/null || true
xcrun simctl uninstall $SIM $BUNDLE 2>/dev/null || true
mkdir -p /tmp/qa/$ISSUE_ID
```

**Fresh device (heavier reset):**
```bash
xcrun simctl shutdown $SIM
xcrun simctl erase $SIM
xcrun simctl boot $SIM
```

**Check sim is alive:**
```bash
xcrun simctl list devices booted | grep -q $SIM && echo booted 

*[truncated — see source for full prompt]*