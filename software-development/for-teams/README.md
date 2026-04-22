# For Teams

> A governance-safe, vendor-neutral foundation for AI-Assisted Development and Agent-Driven workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ai-dev-toolkit for Teams

A governance-safe, vendor-neutral foundation for AI-Assisted Development and Agent-Driven workflows. Built from production experience across 10+ repos, distilled into portable patterns any team can adopt.

## TL;DR

**What it is** — a convention library + executable tooling that turns ad-hoc AI usage into a repeatable, measurable engineering practice.

**What your team gets**
- Consistent skill / rule / agent definitions across projects, so AI tools behave the same way regardless of which IDE or CLI each teammate prefers.
- A local RAG engine that keeps institutional knowledge retrievable in seconds — no context loss between sessions, no repeated questions.
- Lightweight per-feature specs + auto-generated roadmaps that replace stale wikis and Jira drift with a living, git-native source of truth.
- Safe defaults: no third-party SaaS storage, no cloud data egress, all retrieval runs locally from MiniLM embeddings in a SQLite file.

**What your org gets**
- An auditable, in-repo convention layer — rules live in markdown, not hidden in tool configs.
- A compliance story: no Anthropic/OpenAI/Cursor-specific tooling on `main` (that lives on the `personal` branch); `main` is the work-safe surface.
- Shipping velocity: the skills are opinionated about when to use RAG, when to spec, when to ship, and when to stop. Less thrash, more landed PRs.

## The three pillars

### 1. AI-Assisted Development (AAD)
Every skill in `kit/core/skills/` is a "how to use AI for X" playbook — debugging, refactoring, code review, test generation, migration, observability. Skills are markdown-only, so any AI tool that reads project docs (Claude Code, Cursor, Copilot Chat, Codex) picks them up automatically.

### 2. Agent-Driven Development (ADD)
`kit/core/agents.json` + `kit/core/skills/auto-invoke.md` let agents route work to themselves based on task verbs (plan, ship, fix, refactor, review). Teams with custom agent setups (LangGraph, AutoGen, internal tooling) wire i

*[truncated — see source for full prompt]*