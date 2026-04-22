# AGENT COMPLETION GUIDE

> **Repository:** `midnghtsapphire/reese-reviews`
**Author:** Copilot Agent (analysis session April 5, 2026)
**Audience:** Audrey Evans (owner), all AI 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Completion Guide — Why AI Agents Don't Finish Apps (And How to Fix It)

**Repository:** `midnghtsapphire/reese-reviews`
**Author:** Copilot Agent (analysis session April 5, 2026)
**Audience:** Audrey Evans (owner), all AI agents working on this repo

---

## The Problem

> "I am having a real problem getting agents to ship apps that never seem to get all the way done."
> — Audrey Evans, Issue #issue

This is one of the most common frustrations when working with AI coding agents. It is not a bug in the agents — it is a **systems design problem** that can be solved with the right structure. This document explains exactly why it happens and gives you a complete playbook to fix it.

---

## Why Agents Fail to Finish

### 1. No Shared Memory Between Sessions

Every AI agent session starts with a blank slate. When a session ends — whether the agent finishes normally, times out, hits an error, or you close the tab — **everything the agent knew is gone**.

The next agent session (even with the same AI tool) has no idea:
- What was built last session
- What was partially built and left incomplete
- What the next step was supposed to be
- What decisions were made and why

**Result:** Each agent session either starts over from scratch, or picks a random task that seems important based on the code it can see right now — ignoring half-finished work.

**Fix:** Every agent session **must end** by writing a `HANDOFF.md` update. Every agent session **must start** by reading `HANDOFF.md`. This is mandatory, not optional.

---

### 2. Tasks Are Too Large for One Session

Most AI agent sessions have a context window limit (typically 100K–200K tokens) and a time limit. A task like "implement Plaid bank integration" touches 8+ files, requires 3 API calls, and needs unit tests. That is a multi-hour task for a human — it is too large for a single agent session.

**What happens:** The agent starts the work, gets 60% done, hits its context limit or time limit, and exits. The next age

*[truncated — see source for full prompt]*