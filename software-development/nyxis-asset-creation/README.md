# Nyxis Asset Creation

> name: nyxis-asset-creation description: Create, repair, and normalize Nyxis raster game assets, especially monster sprites under `assets/images/icons/**`. Use when a Nyxis sprite has wrong canvas size, wrong aspect ratio, missing transparency, background contamination, or inconsistent framing, or wh

## Tags
`python`

## System Prompt
---
name: nyxis-asset-creation
description: Create, repair, and normalize Nyxis raster game assets, especially monster sprites under `assets/images/icons/**`. Use when a Nyxis sprite has wrong canvas size, wrong aspect ratio, missing transparency, background contamination, or inconsistent framing, or when Codex needs to create a new sprite that matches existing in-game asset conventions.
---

# Nyxis Asset Creation

Create repo-ready bitmap assets for Nyxis. Use fixed Nyxis sprite conventions. Do not re-measure sibling monster assets on each invocation.

## Workflow

1. Apply hardcoded Nyxis sprite rules immediately.
2. If source art is mostly correct but wrong format, repair it instead of regenerating from scratch.
3. If source art cannot be repaired cleanly, generate replacement art that follows hardcoded rules.
4. Verify final asset before replacing repo file.

## Monster Sprite Rules

For `assets/images/icons/monsters/*.png`, use these hardcoded defaults:

- Use `256x320` portrait canvas.
- Use aspect ratio `0.8`.
- Require transparent background with alpha channel.
- Keep single full-body subject centered in frame.
- Optimize for readability at in-game size first.
- Prefer large simple shapes over fine texture.
- Keep silhouette bold and instantly recognizable.
- Keep face, hands, weapon, and defining traits readable after downscaling.
- Keep proportions grounded and fantasy-illustration based, not cartoon or chibi.
- Use adult humanoid proportions with natural head-to-body ratio.
- Prefer serious, menacing, or eerie expression over cute appeal.
- Keep modest edge padding; do not crop hands, feet, weapons, or wings.
- Keep subject scaled to fill most of frame without touching edges.
- Bias subject slightly downward so feet sit near bottom padding.
- Avoid wide landscape compositions.
- Avoid excessive cloth tears, tiny accessories, dense armor detail, micro-texture, and noisy rendering.
- Avoid cinematic detail that disappears when sprite is small.
- Avoid over

*[truncated — see source for full prompt]*