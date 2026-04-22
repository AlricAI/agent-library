# Agent Comment Protocol

> Every specialist posts structured comments on their assigned issue throughout a run.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Agent Comment Protocol

Every specialist posts structured comments on their assigned issue throughout a run. These comments are the human-in-the-loop channel — the CEO and Steve read them in real time to monitor progress, catch blockers, and verify work before merge.

## The 5 Tags

### [START]
Post immediately after picking up the issue, before touching any code.

**What to include:**
- What you understood the issue to be asking (1-2 sentences)
- Which files you plan to modify (file list)
- Estimated time or iteration count

**Example:**
```
[START] FORGE-42: Add cost breakdown chart to dashboard.
Plan: (1) read CostPage.tsx, (2) add BarChart component using recharts, (3) wire Supabase query.
Files: dashboard/src/app/costs/page.tsx. Est: 15 min.
```

---

### [PROGRESS]
Post on every major state transition: after checkout, after each implement phase, after build passes, after push.

**What to include:**
- What just completed
- Whether it succeeded or failed
- What's next

**Example:**
```
[PROGRESS] Build passes (0 errors). About to push branch agent/forge-42-cost-chart and open PR.
```

---

### [BLOCKED]
Post immediately when stuck for more than 2 minutes on any obstacle.

**What to include:**
- Exactly what you tried
- The error or missing information
- 2-3 options for how to unblock (let the COO pick)

**Example:**
```
[BLOCKED] Build fails: "Module not found: recharts". Not in package.json.
Options: (A) run npm install recharts and commit package-lock update, (B) use a different charting lib already installed, (C) wait for COO to approve the dep addition.
```

---

### [PROOF]
Post when the PR is ready, BEFORE calling `gh pr create`. Include concrete artifacts — not assertions.

**MANDATORY: Every [PROOF] comment must be accompanied by at least ONE uploaded artifact** via `POST /api/agent/issues/{id}/attachments` (the one-shot upload endpoint — see "How to Upload an Artifact" below). No upload = no proof. Steve: "I see agents talking but no screenshot

*[truncated — see source for full prompt]*