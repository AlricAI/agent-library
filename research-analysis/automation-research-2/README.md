# Automation Research 2

> **Status:** Planning

**Purpose:** Translate prior automation research into an implementable plan that addresses open questions, outlines responsible 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Automation Implementation Plan

**Status:** Planning

**Purpose:** Translate prior automation research into an implementable plan that addresses open questions, outlines responsible subsystems, and prepares the timeline overhaul for keyframe authoring.

## Guiding Principles

- Preserve determinism by storing automation data in the scene store and evaluating it from tick-aligned playback.
- Treat automation as an extension of existing binding semantics so current scenes remain valid.
- Deliver UX that scales from rapid keyframe drops to advanced curve editing without overwhelming newcomers.

## Architecture Outline

1. **Automation Binding Model**
    - Extend the binding union with `type: 'keyframes'` that references automation channels keyed by `{elementId}.{propertyPath}`.
    - Store channels in a central registry under the scene root; each channel contains ordered keyframes `{ tick, value, easing, handles? }`.
    - When users adjust a property during playback, create (or update) the keyframe at the transport tick, honoring the decision that manual overrides author new automation data.

2. **Curve & Easing Infrastructure**
    - Upgrade `FloatCurve` to a piecewise evaluator supporting linear, stepped, and cubic-handle interpolation.
    - Maintain a preset library (ease-in/out, etc.) and expose custom curves through reusable definitions that can be attached across channels.
    - Cache compiled curve segments per channel and invalidate only on keyframe/easing changes to avoid render-loop regressions.

3. **Evaluation Engine**
    - During playback/export, resolve automation channels at the active tick, convert to normalized segment progress, and apply the upgraded curve evaluator.
    - Surface evaluated values as transient macro-like outputs that the runtime adapter consumes before render.
    - Define precedence: automation result → macro modifier (additive/multiplicative) → constant fallback, ensuring predictable layering between systems.

4. **Timeline & 

*[truncated — see source for full prompt]*