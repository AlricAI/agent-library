# Mcm Forge Orchestration

> > Created: 2026-04-21
> Status: v1 — the durable vision. Read this one file and you understand the whole factory.
> Owner: CEO (laptop session) + Stev

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: MCM Forge Agent Orchestration

> Created: 2026-04-21
> Status: v1 — the durable vision. Read this one file and you understand the whole factory.
> Owner: CEO (laptop session) + Steve (owner)

---

## The Thesis

**MCM Forge is a graph of narrow specialists connected by issue comments, gated by durable artifacts.**

The unit of work is an Issue. The unit of motion is a Heartbeat. The unit of communication is a Comment. The unit of truth is an uploaded Artifact. Everything else — the dashboard, the orchestrator, the AGENTS.md files — is plumbing in service of this shape.

When all four units work together under eight hard rules, a tired operator at 3 am cannot accidentally burn $100 on a broken agent. That's the dummy-proof promise.

---

## The 5 Load-Bearing Components

### 1. The Issue is the atomic unit

An issue is not a "task" and not a "PR." It's the durable container for all work:

- **Spec** — the description
- **Conversation** — comments in the 5-tag grammar (see Component 4)
- **Evidence** — attachments in `forge.issue_attachments` (linked to Supabase storage objects)
- **State** — status / assignee / parent / blockers
- **Ledger** — runs (agent invocations) + issue_events (status changes, reassignments, approvals)

Everything happens on an issue. The dashboard is the control tower.

**Identifier rule:** `FORGE-N` for MCM Forge company, `DIRA-N` for DirtSync company. Prefix mismatch = bug. Enforced by the agent API using `companies.issue_prefix`.

**1 PR = 1 Issue** (from `companies/mcm-forge/PR-RULES.md`). No bundled PRs. No PRs without an issue.

### 2. Specialists, never generalists

Every agent is narrow. Five files define an agent:

| File | Purpose |
|---|---|
| `AGENTS.md` | Identity + scope + frontmatter (company, skills, adapter, model) |
| `HEARTBEAT.md` | Step-by-step lifecycle from wake to exit |
| `TOOLS.md` | Canonical copy-paste commands |
| `LESSONS.md` | Append-only scars (format in `lessons-learned-loop.md`) |
| `GATES.md` | Curre

*[truncated — see source for full prompt]*