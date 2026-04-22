# Tweet Automation Design

> ## Overview

Automated daily social posting system for the bagrounds.org digital garden. A GitHub Actions
workflow runs on a cron schedule each mornin

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Social Post Automation Design Document

## Overview

Automated daily social posting system for the bagrounds.org digital garden. A GitHub Actions
workflow runs on a cron schedule each morning, reads **yesterday's** reflection note from the
repo, uses Google Gemini to generate a post, publishes it to **Twitter/X** and **Bluesky**,
fetches the embed HTML, and writes the updated note back to the **Obsidian vault** via
[Obsidian Headless Sync](https://help.obsidian.md/sync/headless).

Both social platforms are optional — the script posts to whichever platforms have credentials
configured. Platform failures are logged but don't crash the pipeline.

The user reviews the change in Obsidian (e.g. on their phone) and publishes it to this repo via
the Enveloppe plugin, at which point the deploy workflow rebuilds and publishes the site.

## Architecture

```
┌─────────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  GitHub Actions  │────▶│  Read        │────▶│  Gemini API  │────▶│  Twitter API │
│  Cron Trigger    │     │  Yesterday's │     │  Generate    │     │  Post Tweet  │
│  (9 AM Pacific)  │     │  Reflection  │     │  Tweet Text  │     │              │
└─────────────────┘     └──────────────┘     └──────────────┘     └──────┬───────┘
                                                                         │
                        ┌──────────────┐     ┌──────────────┐           │
                        │  Obsidian    │◀────│  oEmbed API  │◀──────────┘
                        │  Headless    │     │  Get Embed   │
                        │  Sync: Pull, │     │  HTML        │
                        │  Update,     │     └──────────────┘
                        │  Push        │
                        └──────┬───────┘
                               │
                        ┌──────▼───────┐     ┌──────────────┐
                        │  User Reviews│────▶│  Enveloppe   │
                        │  in Obsidian │     │  Plugin:     │
          

*[truncated — see source for full prompt]*