# Synth Plan V1

> status: draft



Add a per‑MIDI‑track toggleable synth audition (muted by default) that plays that track’s notes through a lightweight Web Audio–based

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
status: draft

## 1. Goal & Scope

Add a per‑MIDI‑track toggleable synth audition (muted by default) that plays that track’s notes through a lightweight Web Audio–based polyphonic synth synchronized with the existing transport. It must: - Respect transport play/stop, looping, and tempo (including tempo map changes if supported). - Be low CPU, garbage‑light, and not interfere with existing rendering/export systems. - Persist its on/off state with documents. - Require a single user gesture to unlock AudioContext (first activation or global transport start). - Be future‑extensible (envelopes, instrument presets, velocity curves).

## Out of scope (for now): multi‑instrument selection UI, soundfonts, pedal CCs, pitch bend, advanced effects.

## 2. Data Model Changes

Add properties to `TimelineTrack` (only when `type === 'midi'`):

```
interface TimelineTrack {
  // ...existing
  auditionEnabled?: boolean; // user toggled synth playback
  auditionVolume?: number;   // linear 0–1 (default 0.8)
}
```

Defaults: `auditionEnabled = false`, `auditionVolume = 0.8`.

Persistence:

-   Include these fields in: `timelineStore` serialization snapshots, document export/import (document-gateway.ts, export.ts, import.ts).
-   Backward compatibility: default them when undefined.

---

## 3. Synth Architecture (Web Audio)

Create a small “poly manager” per active auditioned track rather than one global poly pool to simplify per‑track volume/gain.

File: `src/state/audio/track-synth.ts` (new folder `audio/` if not present; or reuse `audio-engine.ts` pattern).

Components:

1. Shared `AudioContext` singleton (lazy, created on first need or on global transport start).
2. `TrackSynth` class:
    - Constructor: `(ctx, trackId, options)`; creates a `GainNode` (track bus) feeding a global master gain (optional).
    - Methods:
        - `scheduleNoteOn(note: number, velocity: number, startTime: number, durationSeconds: number)`
        - `flushActive()` (on stop / track disable).
        - `

*[truncated — see source for full prompt]*