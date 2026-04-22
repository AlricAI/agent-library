# VISUAL ROADMAP

> **Quick visual reference for Azure HayMaker enhancement timeline.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Visual Enhancement Roadmap 2025-2026

**Quick visual reference for Azure HayMaker enhancement timeline.**

See [Enhancement Roadmap](ENHANCEMENT_ROADMAP.md) for detailed specifications.

---

## Quarterly Timeline

```mermaid
gantt
    title Azure HayMaker Enhancement Roadmap 2025-2026
    dateFormat YYYY-MM-DD

    section Q1 2026 (P0-Critical)
    SIEM Telemetry Export #124           :crit, siem, 2026-01-06, 3.5w
    Windows VM Security #125             :crit, security, 2026-01-06, 2w

    section Q2 2026 (P1-High)
    Distributed Tracing #127             :trace, 2026-04-01, 2w
    Cost Budget Enforcement #128         :cost, 2026-04-01, 1.5w
    Agent Health Checks #129             :health, 2026-04-15, 2w
    Multi-Tenant Isolation #126          :tenant, 2026-05-01, 6w

    section Q3 2026 (P2-Medium)
    Local Dev Mode #130                  :dev, 2026-07-01, 4w
    GitHub Actions Agent #131            :gh, 2026-08-01, 2w

    section Q4 2026 (P2-Medium)
    Analytics Dashboard                  :dashboard, 2026-10-01, 3w
    Scenario Testing Framework           :testing, 2026-11-01, 4w
```

---

## Impact vs. Effort Matrix

```mermaid
quadrantChart
    title Enhancement Prioritization Matrix
    x-axis Low Effort --> High Effort
    y-axis Low Impact --> High Impact
    quadrant-1 Quick Wins
    quadrant-2 Strategic Investments
    quadrant-3 Consider Deferring
    quadrant-4 May Not Be Worth It

    Windows VM Security (125): [0.15, 0.95]
    SIEM Export (124): [0.5, 0.95]
    Cost Enforcement (128): [0.25, 0.85]
    Circuit Breakers (129): [0.35, 0.70]
    Distributed Tracing (127): [0.30, 0.70]
    Multi-Tenant (126): [0.85, 0.90]
    GitHub Actions (131): [0.35, 0.80]
    Local Dev Mode (130): [0.75, 0.65]
    Analytics Dashboard: [0.50, 0.65]
    Testing Framework: [0.75, 0.60]
```

---

## Dependency Flow

```mermaid
graph TD
    PR119[PR #119: W365 + M365 E2E]
    PR121[PR #121: Windows VM]
    PR123[PR #123: Computer Use]
    PR112[PR #112: KW CLI]

    

*[truncated — see source for full prompt]*