# Brandguide

> > Legacy brand guide artifact.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
> Legacy brand guide artifact. Not canonical for active implementation. Use `lic-design-system/references/` and `docs/PROMPT_CANONICAL_SOURCES.md`.

LIC Brand Guide
Identity summary
Legal Intelligence Corporation (LIC)
Agentic litigation operations for firms: intake → evaluation → drafting → discovery → matter movement → client updates.
Tone: procedural, matte, conservative, reductive.
Brand principles
Systems over slogans
Documentation over decoration
Rules over gradients
Auditability over delight
Quiet confidence
Logo
Official mark: Panelized LIC
Meaning: modular workforce, controlled process, “standards manual” clarity.
Non-negotiable: the three-panel structure prevents “LICE” reads.
Primary SVG (transparent background, for web/app)

Implementation note: using currentColor makes the mark automatically follow your CSS (ink or inverse).
Logo variants
1) App icon (small sizes)
At ≤24px, borders can collapse. Use filled panels + knocked-out letters:

2) Wordmark lockup
Use a strict separator and corporate casing:
LIC (condensed, tracked)
LEGAL INTELLIGENCE CORPORATION (mono or small caps)
Recommended lockup text (UI): LIC / LEGAL INTELLIGENCE CORPORATION
Clear space and minimum size
Clear space: at least one panel stroke width (6 units in the SVG) around the mark.
Minimum size (primary mark):
Web: ≥120px wide
Print: ≥22mm wide
Minimum size (icon variant):
Favicons: 16px (use the filled-panel icon)
Incorrect use
Do not add ticks/stripes to the right of the C.
Do not round corners.
Do not apply shadows, glows, gradients.
Do not skew or compress panels unevenly.
Color
Matte paper + ink + one institutional accent.
Core
Paper: #F2EFE6
Ink: #0B0D0F
Warm Gray: #8B857A
Accent (primary)
Process Blue: #0B3D91
Alert (rare)
Oxide Red: #B23A2B
Usage ratio
Paper 70% / Ink 25% / Accent 5%
Typography
Primary: IBM Plex family (Sans + Sans Condensed + Mono). IBM Plex is available under the SIL Open Font License (OFL).
Headlines: IBM Plex Sans Condensed (uppercase, tracked)
Body/UI: IB

*[truncated — see source for full prompt]*