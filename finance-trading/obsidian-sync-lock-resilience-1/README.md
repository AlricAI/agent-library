# Obsidian Sync Lock Resilience

> ## Overview

This document covers the investigation and fix for intermittent "Another sync
instance is already running" errors in the Obsidian Headles

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Obsidian Sync Lock Resilience

## Overview

This document covers the investigation and fix for intermittent "Another sync
instance is already running" errors in the Obsidian Headless Sync integration.
The error occurred when the auto-post pipeline processed multiple items
sequentially, causing lock contention between consecutive vault sync operations.

## The Problem

When the `auto-post.ts` orchestrator discovers multiple items to post (one per
platform), it calls `main()` sequentially for each. Each `main()` call runs:

1. `syncObsidianVault()` — pull latest vault content
2. Gemini post generation + social media posting
3. `pushObsidianVault()` — push embed sections back to vault

The `ob sync` command (from `obsidian-headless`) uses a `.sync.lock` directory
inside `.obsidian/` to prevent concurrent sync operations. When post N's push
finishes and post N+1's pull starts immediately, lingering processes or lock
artifacts from the push can cause "Another sync instance is already running"
on the pull.

## Root Cause Analysis — 5 Whys (4th Investigation, 2026-03-09)

### 1. Why does "Another sync instance" occur immediately after sync-setup?

Analysis of the `obsidian-headless` source code revealed that **`sync-setup`
does NOT create locks or spawn daemons**. It only writes configuration files
(vault ID, encryption keys, etc.) to a system config directory. The lock error
comes from `ob sync`'s own `acquire()` method failing internally.

### 2. Why does `ob sync`'s own acquire() fail?

The lock class (`Ce` in the minified source) creates a `.sync.lock` directory
via `mkdirSync`, then sets its mtime via `utimesSync`, reads it back with
`statSync`, and compares (`verify()`). If the round-trip mtime doesn't match,
it throws the lock error. **Critically, the lock directory is NOT cleaned up
when `acquire()` fails** — `release()` is only in the inner try-finally, but
acquire failure is caught by the outer catch which just exits.

### 3. Why does the mtime round-trip fail?

*[truncated — see source for full prompt]*