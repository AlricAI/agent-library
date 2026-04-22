# Agent Certification Gates

> > Created: 2026-04-21
> Applies to: every MCM Forge specialist agent
> Rule: **No agent runs at a privilege level higher than its current gate.**

---

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Agent Certification Gates (G1–G5)

> Created: 2026-04-21
> Applies to: every MCM Forge specialist agent
> Rule: **No agent runs at a privilege level higher than its current gate.**

---

## Why this exists

Untested agents running autonomously = wasted money + eroded trust. We were dispatching agents based on "it worked once" as proof. That's not a dial-in. The Certification Gates force explicit, evidenced promotion before each level of autonomy.

Steve's mandate, 2026-04-21 03:45 UTC: *"Don't let them run unless they have been fully tested and dialed in."*

---

## The 5 Gates

| Gate | Name | What it proves | Who signs | Evidence required |
|---|---|---|---|---|
| **G1** | Skill-complete | AGENTS.md + HEARTBEAT + skills frontmatter + LESSONS.md all present and correctly wired | CEO (offline review) | Checklist PASS per section 2 below |
| **G2** | Manual dry-run | Every command in HEARTBEAT works on the Mini when typed by a human | CEO (supervised on Mini) | Annotated transcript of each HEARTBEAT step actually running, posted to the agent's Certification issue |
| **G3** | Supervised live run | One full issue shipped with human in the loop, intervening on first failure | Steve + CEO | `[PROOF]` comment on an issue with ≥1 artifact, human approval |
| **G4** | Match test | Agent reproduces a task that CEO did manually first, to within acceptable diff | CEO (automated check) | Side-by-side diff of manual result vs agent result |
| **G5** | Autonomous clearance | 2+ consecutive G3-quality runs across different issues, zero human intervention required | Steve | Explicit approval comment on the agent's Certification issue |

**No gate skips.** An agent at G1 cannot run on G3-level work. An agent at G4 is still shadowed — Steve spot-checks every dispatch.

---

## 1. Per-agent Certification Issue

Every agent gets one long-lived Forge issue titled:
```
Certification: <Agent Name>
```

- Company: the agent's company (DirtSync or MCM Forge)
- Status stays `in_pro

*[truncated — see source for full prompt]*