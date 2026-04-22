# Feature Request System

> This document explains how feature requests are produced today, why `waveform`/`pitchWaveform` sometimes fail to appear, and a concrete plan for making the pipeline deterministic.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Audio feature request pipeline

This document explains how feature requests are produced today, why `waveform`/`pitchWaveform` sometimes fail to appear, and a concrete plan for making the pipeline deterministic.

## How requests are produced today

1. **Static requirements.** Scene elements register their audio needs at module load using `registerFeatureRequirements` (see `src/audio/audioElementMetadata.ts`). For example, `audio-waveform.ts` and `audio-locked-oscilloscope.ts` both call:

    ```ts
    registerFeatureRequirements('audioWaveform', [{ feature: 'waveform' }]);
    registerFeatureRequirements('audioLockedOscilloscope', [{ feature: 'pitchWaveform' }]);
    ```

2. **Scene element bootstrap.** The `SceneElement` base class (`src/core/scene/elements/base.ts`) invokes `_subscribeToRequiredFeatures()` inside the constructor and whenever `setProperty('audioTrackId', …)` fires. This method pulls the registered requirements, reads the current `audioTrackId`, and calls `syncElementSubscriptions`.

3. **Descriptor normalization.** `syncElementSubscriptions` (`src/audio/features/subscriptionSync.ts`) maps each requirement into a calculator descriptor via `createFeatureDescriptor`, dedupes by identity (`buildDescriptorIdentityKey`), then pushes the list into `syncElementFeatureIntents`.

4. **Per-element intent cache.** `syncElementFeatureIntents` (`src/audio/features/sceneApi.ts`) stores descriptors in an internal `WeakMap` keyed by element object, keeps track of the active track, and calls `publishAnalysisIntent` whenever the descriptor set meaningfully changes. Clearing happens via `clearFeatureData`.

5. **Intent bus.** `publishAnalysisIntent` builds a hashed payload and, if it changed, emits a `publish` event on the analysis-intent bus (`src/audio/features/analysisIntents.ts`). It also applies defaults such as `getDefaultProfile()`.

6. **Consumers.**

    - The audio diagnostics pane (`src/state/audioDiagnosticsStore.ts`) subscribes to the bus to provide UI 

*[truncated — see source for full prompt]*