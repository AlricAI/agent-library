# Performance

> At 900 WPM each word has a 67ms budget.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Performance Spec

At 900 WPM each word has a 67ms budget. Any React render or DOM work that takes longer than ~10ms risks audible/visible timing jitter. The following rules are non-negotiable.

## Timer Drift Compensation

`setTimeout` is not precise — it can fire late by 5–20ms on a loaded JS thread. The scheduler compensates by tracking the nominal expected fire time and subtracting accumulated drift from each next delay:

```ts
const drift = Math.max(0, performance.now() - expectedTime)
const adjustedDelay = Math.max(8, nominalDelay - drift)
timerRef.current = setTimeout(callback, adjustedDelay)
expectedTime += nominalDelay   // advance by nominal, not actual
```

Minimum delay is capped at 8ms to prevent call-stack recursion issues.

## TextPreview — Never Re-render Per Word

`TextPreview` shows a scrolling context of words around the current position. Naïvely re-rendering on every word tick with a large corpus would put thousands of DOM nodes through React's reconciler every 67ms.

**Solution:** Two separate update paths:

1. **React re-renders** — blocked by a custom `memo` comparator that only allows re-renders when `Math.floor(currentIndex / WORDS_PER_LINE)` changes (i.e. once per line ≈ every ~12 words). This shifts the visible window and triggers scroll.

2. **Active word highlight** — updated imperatively via `useImperativeHandle`. The scheduler calls `textPreviewRef.current.updateHighlight(index)` every word. This does a direct `querySelector` + class swap — two DOM operations, zero React involvement.

```ts
// In App.tsx scheduler:
setWordIndex(index)                           // triggers WordDisplay + Controls re-render
textPreviewRef.current?.updateHighlight(index) // updates TextPreview DOM directly
```

### Windowed Rendering

TextPreview only renders a 180-word slice (60 before + 120 after current position). A 100k-word book never has more than 180 spans in the DOM regardless of position.

## PDFPageView

The PDF canvas panel re-renders on `curre

*[truncated — see source for full prompt]*