# PRD Automated Services Audit

> **Author:** Sage + Nova + Bridge (synthesized via parallel audit agents)
**Date:** 2026-04-13
**Status:** Draft v1 — needs product sign-off before exe

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PRD — Automated Services Audit, Wiring Gaps & Monetization Roadmap

**Author:** Sage + Nova + Bridge (synthesized via parallel audit agents)
**Date:** 2026-04-13
**Status:** Draft v1 — needs product sign-off before execution
**Scope:** Every automated service in `team-dashboard` — crons, services, routes, plugins, agents — plus a reality-check on monetization.

---

## TL;DR

- **62 cron jobs** are defined in `server/src/services/*-crons.ts`. **56 wired & healthy**, **5 degraded**, **1 intentionally paused** (Canva), **0 pure stubs**. The central `cron-registry` scheduler is solid.
- **9 "plugin jobs"** claimed in CLAUDE.md are **only 5 really running** — Moltbook's 3 (`content-dispatcher`, `heartbeat`, `daily-cleanup`) + maybe 2 from the registered plugins. **Discord's 2 and Twitter's 4 plugin jobs are dormant** — their manifests exist, but the plugins aren't loaded into the `plugin_config` DB registry, so the plugin-job-scheduler never schedules them. CLAUDE.md overstates the running count.
- **2 orphan services** found: `plugin-log-retention.ts` and `plugin-runtime-sandbox.ts` — exported but never started or imported.
- **~11 of 21 agents are "active"** — i.e. own real executing code. 10 are pure doc-only personas (Atlas, River, Pixel, Core, Flux, Mermaid + most leadership/eng roles). That's fine for task-dispatch roles, but is a gap for anything sold as "automated".
- **Revenue paths: 0 live, 1 near-ready, 3 proof-of-concept, 5 aspirational.** The only thing currently generating trackable output on a recurring schedule is the partner click-tracking system, and it's not billed. **Stripe key is set in env but imported by zero server files.** Partner monthly fees are declared in the DB schema but not wired to payments.
- **Quickest path to first dollar:** wire partner-subscription checkout → Stripe → monthly invoicing cron. ~3-4 days of work. All the upstream plumbing (partner CRUD, metrics, reports, click attribution) already exists.

---

## Table of Contents



*[truncated — see source for full prompt]*