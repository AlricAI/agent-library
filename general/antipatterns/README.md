# ANTIPATTERNS

> **Version**: 1.0.0

Both agents MUST check this catalog before finalizing each round.
The judge SHOULD cite AP-IDs when a finding matches a known anti

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Anti-Patterns Catalog

**Version**: 1.0.0

Both agents MUST check this catalog before finalizing each round.
The judge SHOULD cite AP-IDs when a finding matches a known anti-pattern.
Either agent SHOULD propose new anti-patterns when a recurring mistake is identified.

## How to Use This File

- **Builder**: Scan before marking `ready_for_judge`. If your output matches any symptoms, fix it first.
- **Judge**: When writing findings, check if the issue matches a cataloged anti-pattern. If so, cite the AP-ID alongside the finding ID (e.g., "H-1 (AP-003): ...").
- **After each round**: Both agents should check whether the round's findings reveal a new anti-pattern worth cataloging.
- **New entries**: Append to the bottom. Use the next available AP-ID. Follow the template below.

## Entry Template

```
## AP-NNN: Short Name

**Applies to**: builder | judge | both
**Phase**: specify, design, plan, build, test, release
**Severity**: blocker | high | medium

**Symptoms**:
- How to detect this in an artifact

**Problem**: Why this is harmful.

**Root cause**: Why agents fall into this trap.

**Correct pattern**: What to do instead.

**First observed**: task-id, round N
```

---

## AP-001: Unverified Verification

**Applies to**: builder
**Phase**: design, build
**Severity**: high

**Symptoms**:
- Verification section cites a source (README, docs, API reference) but the claim doesn't match what the source actually says
- "Confirmed via X" without having actually checked X
- Verification claims that are copy-pasted assumptions, not checked facts

**Problem**: False verification is worse than no verification — it gives the judge (and the coordinator) false confidence that a design decision is grounded. When the judge independently checks the source and finds a mismatch, trust erodes and rounds are wasted.

**Root cause**: The builder wants to appear thorough and fills in the Verification section with plausible-sounding claims rather than actually visiting the source.

**Corr

*[truncated — see source for full prompt]*