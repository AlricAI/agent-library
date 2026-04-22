# Speed Reading

> ## RSVP (Rapid Serial Visual Presentation)

Words are shown one at a time in a fixed focal zone. The reader's eye never moves — comprehension comes fr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Speed Reading Spec

## RSVP (Rapid Serial Visual Presentation)

Words are shown one at a time in a fixed focal zone. The reader's eye never moves — comprehension comes from the word coming to the eye rather than the eye scanning text. The top third of the screen is entirely dedicated to this focal zone.

## ORP (Optimal Recognition Point)

Research (O'Regan 1992, Rayner et al. 2016) shows the eye naturally fixates ~30% into a word. Sprint Read always places this character at the exact horizontal centre of the screen using a split-text layout:

```
[before]  [ORP letter]  [after]
right-aligned   ↑   left-aligned
             screen centre
```

Implementation: `src/utils/orp.ts`

```
Word length → ORP index
1–2  chars  → 0  (first char)
3–4  chars  → 1
5–6  chars  → 2
7–9  chars  → 3
10–13 chars → 4
14+  chars  → 5
```

`splitWordAtOrp(word)` returns `{ before, orp, after }`. The ORP letter is rendered in red (`--orp-color: #e74c3c`) with a subtle glow.

**Critical:** `.orp-word` must have **no CSS `opacity` or `transition`**. At 900 WPM each word displays for ~67ms. A 55ms fade causes words to vanish before they register. Instant swap is correct.

## Font Size

`font-size: clamp(3.6rem, 10vw, 6rem)` — targets ~58–96px on phone screens. Research suggests 0.5–1° visual angle per character at arm's length; larger glyphs reduce cognitive load at high WPM. Guide lines at ±62px bracket the cap height of this font size.

## WPM Ramp

Speed ramps from `minWpm` to `maxWpm` over a fixed 60-second wall-clock window (not a fixed word count). This ensures the ramp always feels the same regardless of document length.

```ts
rampProgress = clamp(elapsedMs / 60_000, 0, 1)
easedProgress = easeInOut(rampProgress)   // cubic ease-in-out
currentWpm = minWpm + easedProgress * (maxWpm - minWpm)
delayMs = (60_000 / currentWpm) * getWordMultiplier(word)
```

The delay table is computed once at play start (`buildDelayTable`) and reused until speed settings change or playback restarts.

**D

*[truncated — see source for full prompt]*