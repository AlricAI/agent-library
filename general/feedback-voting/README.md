# Feedback Voting

> When you rate an agent's response with **Helpful** (thumbs up) or **Needs work** (thumbs down), Paperclip saves your vote locally alongside your running instance.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Feedback Voting — Local Data Guide

When you rate an agent's response with **Helpful** (thumbs up) or **Needs work** (thumbs down), Paperclip saves your vote locally alongside your running instance. This guide covers what gets stored, how to access it, and how to export it.

## How voting works

1. Click **Helpful** or **Needs work** on any agent comment or document revision.
2. If you click **Needs work**, an optional text prompt appears: _"What could have been better?"_ You can type a reason or dismiss it.
3. A consent dialog asks whether to keep the vote local or share it. Your choice is remembered for future votes.

### What gets stored

Each vote creates two local records:

| Record | What it contains |
|--------|-----------------|
| **Vote** | Your vote (up/down), optional reason text, sharing preference, consent version, timestamp |
| **Trace bundle** | Full context snapshot: the voted-on comment/revision text, issue title, agent info, your vote, and reason — everything needed to understand the feedback in isolation |

All data lives in your local Paperclip database. Nothing leaves your machine unless you explicitly choose to share.

When a vote is marked for sharing, Paperclip immediately tries to upload the trace bundle through the Telemetry Backend. The upload is compressed in transit so full trace bundles stay under gateway size limits. If that immediate push fails, the trace is left in a retriable failed state for later flush attempts. The app server never uploads raw feedback trace bundles directly to object storage.

## Viewing your votes

### Quick report (terminal)

```bash
pnpm paperclipai feedback report
```

Shows a color-coded summary: vote counts, per-trace details with reasons, and export statuses.

```bash
# Installed CLI
paperclipai feedback report

# Point to a different server or company
pnpm paperclipai feedback report --api-base http://127.0.0.1:3000 --company-id <company-id>

# Include raw payload dumps in the report
pnpm paperclipai f

*[truncated — see source for full prompt]*