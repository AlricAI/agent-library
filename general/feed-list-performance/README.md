# FEED LIST PERFORMANCE

> This document explains why the home feed can feel slow once there are more than ~15 items **even though the screen uses `FlatList`**, and summarizes cross‑platform list best practices.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Feed list performance — research notes

This document explains why the home feed can feel slow once there are more than ~15 items **even though the screen uses `FlatList`**, and summarizes cross‑platform list best practices. It complements product tickets that track concrete remediation work.

## Why `FlatList` alone is not enough

`FlatList` (and `SectionList`) **virtualize**: they only mount native views for a window around the visible viewport. That saves memory versus a `ScrollView` that lays out every child up front.

It does **not** remove these costs:

1. **Per-row work** — Every cell that mounts still runs React reconciliation, layout, and any expensive subtrees (images, markdown, gestures, animations, portals).
2. **Variable heights** — When item heights are unknown or change after mount (e.g. image `onLoad` updating layout), the list must **remeasure** and adjust offsets. That shows up as jank when scrolling or when many images resolve at once.
3. **Overscan** — React Native still renders **more than one screen** of rows above/below the viewport (`windowSize` defaults to `21` in units of viewport height). Heavy rows × overscan = noticeable main-thread load on any device.

So “we use FlatList” answers **memory for huge lists**, not **cost per row** or **layout stability**.

## What the current feed implementation is doing

The following are **observations tied to this repo**, not accusations — together they explain why ~15+ rows can already feel heavy.

### 1. Heavy content inside every visible row

`FeedListItem` wraps `EntryCard`, which for normal rows renders:

- **`MarkdownRenderer` → `EnrichedMarkdownText` (`react-native-enriched-markdown`)** — markdown parsing and rich text for the summary on **every** card. Feed excerpts are a hot path; full markdown stacks are often overkill for a two‑line preview.
- **`CollapsibleClamp` in `fade-only` mode** — still composes clamped layout, gradients, and (for expandable mode elsewhere) Reanimated. Even `fade-onl

*[truncated — see source for full prompt]*