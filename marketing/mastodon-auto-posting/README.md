# Mastodon Auto Posting

> ## Overview

This document covers the Mastodon integration added to the social posting pipeline.
Mastodon posts are created in parallel with Twitter a

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Mastodon Auto-Posting Setup Guide

## Overview

This document covers the Mastodon integration added to the social posting pipeline.
Mastodon posts are created in parallel with Twitter and Bluesky — all three platforms
run concurrently via `Promise.allSettled()`, and each platform is optional and non-fatal.

The Mastodon embed is written to the Obsidian note as an `## 🐘 Mastodon` section
(similar to `## 🐦 Tweet` and `## 🦋 Bluesky`), using Mastodon's iframe-based oEmbed
format. Edits to the reflection note are serialized to avoid conflicts.

## Architecture

```
                                   ┌──────────────┐
                              ┌───▶│  Twitter API  │───▶ oEmbed / local embed
                              │    │  (optional)   │
┌─────────────┐   ┌────────┐  │    └──────────────┘
│  Read       │──▶│ Gemini │──┤
│  Reflection │   │ Generate│  │    ┌──────────────┐
└─────────────┘   │ Post   │  ├───▶│  Bluesky API  │───▶ oEmbed / local embed
                  └────────┘  │    │  (optional)   │
                              │    └──────────────┘
  All three post in           │
  parallel, non-fatal         │    ┌──────────────┐
                              └───▶│  Mastodon API │───▶ oEmbed / local embed
                                   │  (optional)   │
                                   └──────────────┘
```

After all platforms complete, successful embeds are written to the Obsidian note
sequentially (to avoid file write conflicts), then pushed via Obsidian Headless Sync.

## Environment Variables

### Required GitHub Actions Secrets (for Mastodon)

| Secret Name | Description | How to Obtain |
|---|---|---|
| `MASTODON_INSTANCE_URL` | Mastodon instance URL | e.g. `https://mastodon.social` or `https://fosstodon.org` |
| `MASTODON_ACCESS_TOKEN` | Mastodon access token | Settings → Development → New Application → Access Token |

Both must be set to enable Mastodon posting. If either is missing, the script
logs a message and skips Mastodon (non-fatal).

*[truncated — see source for full prompt]*