# First Principles Mvp Report

> Archived note: this memo reflects an older qualification-first product thesis.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Blueprint First-Principles MVP Report

Archived note: this memo reflects an older qualification-first product thesis.
It is kept as historical strategy context only and is not the current public product direction of `Blueprint-WebApp`.

Current product direction:

1. capture supply through `BlueprintCapture`
2. site-specific world models and hosted access as the primary sell
3. qualification / readiness as an optional support layer, not the main story

Date: 2026-03-10

Status: Internal working memo

## Executive summary

Blueprint's MVP should be a **qualification platform**, not a marketplace, not a capture gig network, and not a robot adaptation lab by default.

The default product should be a standardized intake-to-decision pipeline:

1. An operator submits a site, task, and constraints.
2. Blueprint collects guided evidence for the exact task zone.
3. Blueprint runs automated QA, completeness checks, scoping, and risk extraction.
4. Blueprint produces a structured qualification record.
5. Human review handles low-confidence, high-risk, incomplete, or externally shared cases.
6. Qualified sites emit a match-ready opportunity handoff.
7. Only then can a site move into scene-package generation, evaluation, or adaptation work.

That is the important change. The default Blueprint output is not a scene artifact. It is a reusable qualification record plus a routing object.

The current stack is real. The problem is that the center of gravity is wrong. The public WebApp still carries marketplace assumptions. The capture app still behaves like a nearby-target and reservation system. `BlueprintCapturePipeline` is still defined around sim-ready scene assembly. `BlueprintValidation` is explicitly centered on policy trust, world-model adaptation, and PolaRiS-backed evaluation. Those are later-stage systems. The missing MVP is the qualification layer in the middle.

NuRec should stay in the architecture, but it should stop defining the product. It should become a bounded f

*[truncated — see source for full prompt]*