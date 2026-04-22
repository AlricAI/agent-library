# ARMADA

> *Evaluating which first agent unlocks the most future agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ARMADA.md — Agent Armada Architecture

*Evaluating which first agent unlocks the most future agents.*

## Target Armada

| Agent | Role | Hardware | Complexity | Dependencies |
|-------|------|----------|-----------|-------------|
| **Portal1** (exists) | Media librarian, toolmaker | Pi 5 + Hailo + camera | High | None — already running |
| **CTO/PM** | Co-founder, project coordinator | Pi or Mac | Medium | Needs agents to coordinate |
| **Trader** | Crypto trading (Base + Solana) | Pi or cloud | High | APIs, wallets, risk mgmt |
| **Researcher** | Web scouting, digests, newsletters | Pi or Mac | Medium | Web access, sub-agents |
| **Future N** | TBD | Any | Varies | Varies |

## Evaluation: Which First?

### Criteria
1. **Unlock power** — does it make launching agent #3, #4, #5 easier?
2. **Simplicity** — can we learn teaching on something manageable?
3. **Standalone value** — is it useful on its own, even if we never launch another?
4. **Infrastructure it builds** — does the process of creating it produce reusable systems?
5. **Hardware fit** — does it run well on a bare Pi?

### Assessment

#### Researcher
| Criteria | Score | Why |
|----------|-------|-----|
| Unlock power | ★★★★ | Its OUTPUT (research) directly helps design every other agent |
| Simplicity | ★★★★ | Clear loop: go find things → organize → report back |
| Standalone value | ★★★★★ | Daily digest is immediately useful to Mudpaw |
| Infrastructure it builds | ★★★☆ | QMD sharing, sub-agent spawning, report generation |
| Hardware fit | ★★★★★ | Bare Pi + internet. No peripherals needed |
| **Total** | **21/25** | |

**Why it might be first:** Simplest useful loop. Input = curiosity, output = organized knowledge. Exercises the exact teaching muscles we need (onboarding, QMD sharing, communication). Immediately valuable — Mudpaw gets daily research digests from day 1. And its research output helps us design every subsequent agent better.

#### CTO/PM
| Criteria | Score | Why |
|----------|-------|----

*[truncated — see source for full prompt]*