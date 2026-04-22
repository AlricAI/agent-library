# Chord Estimator Research 1

> Feedback highlighted that the existing chord estimator feels inaccurate and hard to trust.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Chord Estimator Research 1

Feedback highlighted that the existing chord estimator feels inaccurate and hard to trust. I reviewed the element UI, the `computeChromaFromNotes` pipeline, and the `estimateChordPB` heuristics to pinpoint where perception diverges from the actual harmony. Below are the main friction points and concrete improvement ideas.

## 1. Static, ultra-short analysis window
- The element defaults to a 0.1 s window and clamps values to a minimum of 0.05 s, always centered around the current frame ([src/core/scene/elements/midi-displays/chord-estimate-display.ts#L87-L96](src/core/scene/elements/midi-displays/chord-estimate-display.ts#L87-L96), [src/core/scene/elements/midi-displays/chord-estimate-display.ts#L353-L355](src/core/scene/elements/midi-displays/chord-estimate-display.ts#L353-L355)).
- Because the window is symmetric around `targetTime`, the algorithm “looks ahead” into notes that the audience has not heard yet when the playhead is near the start of a chord, contributing to labels that feel premature.

**Improvements**
1. Allow asymmetric windows (e.g., 80% past / 20% future) to bias detection toward already-audible notes.

## 2. Chroma normalization removes intensity & register cues
- `computeChromaFromNotes` accumulates overlap × velocity weights but normalizes the chroma so the total energy always sums to 1.0 ([src/core/midi/music-theory/chord-estimator.ts#L20-L43](src/core/midi/music-theory/chord-estimator.ts#L20-L43)).
- Normalization discards absolute energy and dynamic contrast: a ghost note transient exerts the same influence as a sustained pad, and quiet pickup notes can flip the detected root as soon as they enter the window.
- Bass emphasis is limited to selecting the single lowest MIDI note in the window; sustained bass notes lose influence if the upper structure keeps changing, which feels wrong musically.

**Improvements**
1. Keep both normalized chroma and absolute energy so low-energy windows can be down-weighted or labele

*[truncated — see source for full prompt]*