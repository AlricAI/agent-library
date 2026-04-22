# UX SPECIFICATION

> ## Executive Summary

Flovey is a parent-child financial education mobile app targeting two age cohorts (6-9, 10-14) with mission-driven engagement lo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Flovey MVP - UX & Learning Journey Specification

## Executive Summary

Flovey is a parent-child financial education mobile app targeting two age cohorts (6-9, 10-14) with mission-driven engagement loops. Children learn money management through task-to-reward flows, savings goals, and patience challenges. Parents maintain oversight through a dashboard, reminders, and progress reporting.

---

## Platform & Architecture

**Target Platform:** iOS + Android (React Native + Expo)
**Offline Support:** Core flows with eventual sync
**Minimum Touch Targets:** 48px (thumb-zone optimized)
**Navigation:** Tab-based (child) + Stack (parent)

---

## Age Cohort Strategy: 6-9 vs 10-14

### Age 6-9 ("Seedling" Cohort)
- **Cognitive:** Concrete operations, instant gratification bias, early number sense
- **Engagement:** Bright colors, emoji, celebration loops, daily streaks
- **Learning Focus:** Cause-effect (task→reward), object permanence (savings), patience in small doses (1-7 day challenges)
- **Vocabulary:** "Coins," "Treasure," "Magic Plant," "Helpers"
- **Parent Role:** High oversight (all actions require approval or monitoring)

### Age 10-14 ("Navigator" Cohort)
- **Cognitive:** Formal operations emerging, future planning, peer awareness
- **Engagement:** Progress milestones, peer achievements, strategic planning UI
- **Learning Focus:** Time-value, opportunity cost, compound growth simulation
- **Vocabulary:** "Balance," "Portfolio," "Dividends," "Investment"
- **Parent Role:** Guardrails + autonomy (approve goal categories, monitor summaries)

---

## Onboarding Journey

### Phase 1: Family Account Setup (Parent-Led, ~5 minutes)

**Screen Sequence:**

1. **Welcome Screen**
   - Parent role: Create account
   - Biometric or PIN setup
   - Visual: Single parent illustration (diverse representation)

2. **Child Registration**
   - Parent adds 1+ children (age, name, photo)
   - Age determines cohort + feature set
   - Confirm parental custody/relationship

3. **Quick Set

*[truncated — see source for full prompt]*