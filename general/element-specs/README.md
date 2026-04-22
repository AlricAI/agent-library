# Element Specs

> When designing these for baked animation, your aim is not measurement precision but **readability, expressiveness, coherence, and control over “emotion”**.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## Goals (for video / rendered visualizers)

When designing these for baked animation, your aim is not measurement precision but **readability, expressiveness, coherence, and control over “emotion”**. The visualizations should:

-   React responsively to audio without being noisy or jittery.
-   Maintain legibility (users watching video snapshots or transitions should see meaningful structure).
-   Support stylistic variation (e.g. calm, aggressive, pastel, neon).
-   Be exportable at arbitrary resolution / framerate.

Thus: expose enough control so creators tune feel; hide any interactive UI gimmicks.

---

## Module: Spectrum Display (FFT / spectral bars / curves)

### What it shows / behavior

-   A transform-based view of spectral magnitude vs frequency, rendered as a line, area, bars, or hybrid.
-   Smooth temporal transitions so motion is fluid.
-   Optional peak-history glow or trace accent to emphasize strong frequencies over time.
-   (Optional) spectral balancing or weighting (e.g. tilt bass/treble) for “stylistic boost.”

### Controls (parameters) to expose

Here’s a recommended set of parameters your user could tweak when authoring a visualization:

| Parameter                                  | Type / Range                                                                     | Description / Role in the visual                                                                                                                                                                                                                                     | Suggested default / usability tip                    |
| ------------------------------------------ | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*[truncated — see source for full prompt]*