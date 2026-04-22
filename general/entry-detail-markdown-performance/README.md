# ENTRY DETAIL MARKDOWN PERFORMANCE

> ## What you have today

Entry detail (`EntryDetailScreen`) renders markdown in two places:

| Location | Component | `MarkdownRenderer` variant | Note

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Entry detail markdown performance — research notes

## What you have today

Entry detail (`EntryDetailScreen`) renders markdown in two places:

| Location | Component | `MarkdownRenderer` variant | Notes |
|----------|-----------|----------------------------|--------|
| **Content** (main article) | `EntryMarkdownBody` | **`body` (default)** | Full `entry.content`; LaTeX enabled via `md4cFlags` (`latexMath: true`). |
| **Summary** | `EntrySummaryCard` | **`excerpt`** | Shorter TLDR; LaTeX off; wrapped in **`CollapsibleClamp`** (expand/collapse + Reanimated). |

Both use **`react-native-enriched-markdown`** (`EnrichedMarkdownText`), which parses Markdown with **md4c** and builds a **native** text/layout tree. That is powerful (GFM-style features, math, selection on body) but **work scales with document size**: long `entry.content` means a larger parse and more native nodes in a **single** subtree.

The screen uses a normal **`Animated.ScrollView`**: the body is **not virtualized**. Everything below the hero (header, summary, key points, **full markdown body**, etc.) is in one scrollable document, so the heavy markdown tree is mounted when the screen renders (modulo React scheduling), not on demand per viewport.

## Why it can feel slow even on high-end devices

1. **CPU-bound parse + layout** — One large string → one large native markdown result. JS thread and native layout both do meaningful work at mount and on content updates (e.g. refetch while processing).
2. **LaTeX path on the body** — Even when the article has no math, the **`body`** variant keeps **`latexMath: true`** in `MarkdownRenderer`, so the pipeline may still pay for math-capable parsing/rendering unless the library short-circuits aggressively internally.
3. **Summary card overhead** — `CollapsibleClamp` adds measurement, gradients, and **Reanimated** height animation around the summary markdown. That is extra work on top of the renderer for a smaller string, but it still matters for first paint and 

*[truncated — see source for full prompt]*