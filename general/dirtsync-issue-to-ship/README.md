# dirtsync-issue-to-ship

> The COMPLETE checklist for DirtSync iOS work. From reading the Forge issue to posting proof. Every step must be followed in order. No skipping.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DirtSync: Issue to Ship

This is your step-by-step checklist. Follow it IN ORDER. Do not skip steps. Do not rearrange. Each step must be completed before moving to the next.

---

## Step 0: Setup (once per session)

```bash
export SUPA_KEY=$(grep SUPABASE_SERVICE_ROLE_KEY /Users/stevemcmillian/llama-3-agents/Apps/projects/MCMForge/forge-orchestrator/.env | cut -d= -f2-)
export SUPA_URL="https://ncwxeeqvujgyiggkviqq.supabase.co"
export COMPANY_ID="99338dee-5fdc-4cbf-a344-5c08ec112a2b"
```

Verify it works:
```bash
curl -s "$SUPA_URL/rest/v1/issues?company_id=eq.$COMPANY_ID&status=eq.todo&select=id,title&limit=3" \
  -H "apikey: $SUPA_KEY" -H "Authorization: Bearer $SUPA_KEY" -H "Accept-Profile: forge"
```

If you see issues, you're connected. If empty or error, STOP and fix auth.

**How to "Post to issue"** — use this for EVERY step that says "Post to issue":
```bash
curl -s "$SUPA_URL/rest/v1/issue_comments" -X POST \
  -H "apikey: $SUPA_KEY" -H "Authorization: Bearer $SUPA_KEY" \
  -H "Content-Type: application/json" -H "Content-Profile: forge" \
  -d "{\"issue_id\":\"<ISSUE_ID>\", \"company_id\":\"$COMPANY_ID\", \"body\":\"<YOUR_COMMENT>\"}"
```
**CRITICAL:** `company_id` is required (NOT NULL). Omitting it will silently fail.

---

## Step 0.5: Search Knowledge Base

Before reading the issue, check if prior knowledge exists for the problem area:
```bash
# Search by tags relevant to your issue (adjust tags for your domain)
curl -s "$SUPA_URL/rest/v1/knowledge?tags=cs.{RELEVANT_TAG}&confidence=neq.disproven&select=title,body,tags,confidence" \
  -H "apikey: $SUPA_KEY" -H "Authorization: Bearer $SUPA_KEY" -H "Accept-Profile: forge" | python3 -m json.tool
```

Common tags: `maplibre`, `poi`, `trail-detection`, `hud`, `ride-recording`, `zoom`, `simulator`, `xcodebuild`, `supabase`, `gpx`

If results come back:
- **Read them.** Apply proven knowledge before attempting your own fix.
- **If a prior attempt is marked `disproven`, do NOT repeat it.**

If no results: pro

*[truncated — see source for full prompt]*