# KUNG FU DEMO

> > The 30-second demo that shows instant Elasticsearch mastery in Cursor.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# "I Know Kung Fu" Demo

> The 30-second demo that shows instant Elasticsearch mastery in Cursor.

## The Pitch

**Before:** "I don't know how to query Elasticsearch, write ES|QL, or build observability workflows."

**After (30 seconds later):** "I know kung fu."

## Setup (One-Time, 10 seconds)

### In Cursor

1. Press `Cmd+Shift+J` (Mac) or `Ctrl+Shift+J` (Windows/Linux)
2. Click **Rules** → **Add Rule** → **Remote Rule (GitHub)**
3. Paste: `https://github.com/bahaaldine/moltler.git`
4. Done.

That's it. No npm install. No configuration. No API keys needed for the demo.

## The Demo Script (20 seconds)

### Scene 1: The Setup

Open Cursor chat and type:

```
What can you do with Elasticsearch?
```

**Agent responds** with the full capability matrix - 320+ functions across observability, security, search, ML, and more.

### Scene 2: The "I Know Kung Fu" Moment

Type:

```
/kung-fu
```

**Agent shows** the instant mastery message with all capabilities unlocked.

### Scene 3: Prove It Works

Type any of these:

```
Check my cluster health
```
→ Agent runs `ES_CLUSTER_HEALTH()` and explains the results

```
Find errors in the last hour
```
→ Agent writes and executes ES|QL query

```
What services are throwing the most exceptions?
```
→ Agent builds an aggregation query and analyzes results

### Scene 4: Advanced Capabilities

```
If CPU goes above 80%, send a Slack alert
```
→ Agent creates an alert rule with Slack action

```
Hunt for this IP across all security indices: 10.0.0.50
```
→ Agent runs threat hunting query

```
Summarize today's incidents using AI
```
→ Agent uses LLM to analyze and summarize

## Live Demo Checklist

- [ ] Elasticsearch running (can use `./scripts/quick-start.sh`)
- [ ] Cursor with Moltler rules installed
- [ ] Sample data loaded (quick-start.sh does this automatically)

### Quick Start for Demo

```bash
# Clone and start everything
git clone https://github.com/bahaaldine/moltler.git
cd moltler
./scripts/quick-start.sh

# In another term

*[truncated — see source for full prompt]*