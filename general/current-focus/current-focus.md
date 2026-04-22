---
name: Current Focus
description: Active work and next priorities
model: claude-sonnet-4-5
---
## Active Work

- **VID-15** (high, in_progress): First real article-to-video generation -- test article in French. Assigned to Founding Engineer.
  - Both episodes failed at script generation (`script_done: false`)
  - **Root cause found (CEO):** `.env` had an undersized model configured -- too small for structured JSON generation. Fixed to use the standard 9B model.
  - FE's code changes are solid: content-aware script gen, VRAM coordination, configurable validation
  - FE needs to: commit changes, clear stale checkpoints, re-run with fixed model

## Next Up (Sprint 2 candidates)

- VID-10: External video provider (plan exists, backlog, assigned to board)
- Duration control: validate +/-5% of target
- Subtitles V2: background box, scale bounce, adaptive sizing
- X/Twitter thread parser
- Trending topic discovery

**Why:** Board wants proof the pipeline works end-to-end on real content. VID-15 is the validation gate before Sprint 2 feature work.
**How to apply:** All Sprint 2 planning blocked on VID-15 results. Don't start new feature work until we have a real video.