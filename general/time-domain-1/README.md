# Time Domain

> Authoritative domain: **ticks** (integer).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Time Domain Architecture

Authoritative domain: **ticks** (integer). Seconds are a _derived_ presentation & scheduling view
computed through the shared `TimingManager` using the tempo map + global BPM fallback.

## Canonical Concepts

| Concept                       | Stored Field(s)                                        | Notes                                                               |
| ----------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------- |
| Playhead                      | `timeline.currentTick`                                 | Always integer tick.                                                |
| Loop Range                    | `transport.loopStartTick`, `transport.loopEndTick`     | Optional; inclusive start, exclusive end semantics for comparisons. |
| Timeline View Window          | `timelineView.startTick`, `timelineView.endTick`       | UI pan/zoom.                                                        |
| Playback Range (Scene Bounds) | `playbackRange.startTick`, `playbackRange.endTick`     | Optional explicit scene trimming.                                   |
| Track Offsets                 | `tracks[id].offsetTicks`                               | Applied additively to note start/end ticks for global position.     |
| Notes                         | `note.startTick`, `note.endTick`, `note.durationTicks` | Ingest normalizes to canonical PPQ.                                 |

No seconds (`currentTimeSec`, `loopStartSec`, `offsetSec`, etc.) or beats fields are persisted in state. Beats/seconds are computed on demand.

## Conversion Flow

```
             +--------------+            +------------------+
     tick -> | TimingManager| -> beats ->| Tempo Segments   | -> seconds
             +--------------+            +------------------+
```

Fast paths:

-   Fixed tempo (no map): seconds = ticks / TPQ \* (60 / BPM)
-   Tempo map: piecewise inte

*[truncated — see source for full prompt]*