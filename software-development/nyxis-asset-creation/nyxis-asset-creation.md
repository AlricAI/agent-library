---
name: Nyxis Asset Creation
description: name: nyxis-asset-creation description: Create, repair, and normalize Nyxis raster game assets, especially monster sprites under `assets/images/icons/**`. Use when a Nyxis sprite has wrong canvas size, wrong aspect ratio, missing transparency, background contamination, or inconsistent framing, or wh
---
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
- Avoid oversized heads, toy-like bodies, exaggerated cute facial design, and cartoon simplification.
- Avoid white, black, or painted backdrop fills.
- Export as `.png`.

These defaults are project rules. Do not inspect peer assets each run unless user explicitly asks to revise style contract. Background reference lives in [references/monster-sprite-spec.md](references/monster-sprite-spec.md).

## Repair Existing Art

Use [scripts/normalize_monster_sprite.py](scripts/normalize_monster_sprite.py) when source art already has usable subject but wrong canvas or non-transparent background. Script assumes Nyxis monster defaults and should be used without re-deriving canvas rules.

Default repair workflow:

```bash
python scripts/normalize_monster_sprite.py --input <source.png> --output <fixed.png>
```

Script behavior:

- Remove near-white flat background into alpha.
- Auto-crop visible subject bounds.
- Scale subject to fit `256x320` canvas with padding.
- Center subject horizontally and bias slightly toward bottom like existing monster art.

## Create New Art

When making new monster art from scratch:

- Match established Nyxis monster framing and readability contract before matching fine detail.
- Ask for or enforce transparent background.
- Prefer readable silhouette at small in-game size over high-detail scene art.
- Simplify costume, anatomy, and materials so monster still reads at distance.
- Emphasize one or two defining features, not many small ones.
- Keep subject value contrast strong enough to survive downscaling.
- Preserve fantasy tone and believable humanoid proportions.
- Anchor style with positive target descriptors before adding avoid-list guardrails.
- Assume humanoid monsters use same `256x320` transparent portrait format unless user explicitly says otherwise.

Use this hardcoded base prompt scaffold for Nyxis monster generation:

```text
Use case: stylized-concept
Asset type: Nyxis monster sprite
Primary request: <monster description>
Style/medium: fantasy character illustration for a 2D roguelike sprite, painterly game-art look, readable but not cartoon
Composition/framing: single centered full-body character, portrait framing, fits cleanly inside a 256x320 crop, no limbs or weapon cut off
Lighting/mood: clear fantasy lighting with strong silhouette readability
Color palette: restrained fantasy palette with strong local contrast
Constraints: adult humanoid proportions, natural head-to-body ratio, serious menacing presence, transparent background, no scene background, no text, no watermark, no extra characters
Avoid: wide composition, painted backdrop, cropped extremities, tiny distant subject, excessive micro-detail, noisy textures, tiny accessories, overly intricate costume detail, cartoon style, chibi proportions, oversized head, cute character design
```

For humanoid undead or warrior variants, keep these defaults unless user overrides them:

- full-body pose
- centered subject
- portrait output
- transparent background
- sprite readability over cinematic detail
- simple readable shapes over ornate detail
- grounded fantasy proportions over cartoon stylization
- positive style anchors first, negative guardrails second
- no environmental scene

If using image generation CLI, pair this prompt with:

- size `1024x1536`
- quality `low`
- output format `png`
- transparent background when supported

Do not invent new framing rules per request. Start from this prompt scaffold and only swap subject-specific details.

## Verify Final Asset

Check all:

- PNG loads successfully.
- Canvas `256x320`.
- Alpha channel present.
- Subject readable on both light and dark checkerboard.
- No leftover matte halo from background removal.
- File path and name match in-game config.