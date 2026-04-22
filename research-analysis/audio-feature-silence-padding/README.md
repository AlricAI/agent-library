# Audio Feature Silence Padding

> ## Snapshot

-   Elements request audio-reactive data through `getFeatureData` in `src/audio/features/sceneApi.ts`.
-   Feature descriptors funnel thr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Audio feature data flow and virtual silence handling

## Snapshot

-   Elements request audio-reactive data through `getFeatureData` in `src/audio/features/sceneApi.ts`.
-   Feature descriptors funnel through `FeatureSubscriptionController`, which publishes analysis intents and manages per-element cache bindings.
-   Audio feature caches are generated async via `sharedAudioFeatureAnalysisScheduler` and stored in the `timelineStore` under `audioFeatureCaches`.
-   Sampling happens in `sampleFeatureFrame` → `getTempoAlignedFrame`, which currently yields zeroed frames and sometimes truncated waveform vectors when the request falls outside the analysed buffer.
-   We can emulate pre/post-track silence without inflating cache size by synthesising silent frames on demand using cached shape metadata rather than storing extra frames in the cache itself.

## 1. From element requests to cached feature tracks

### 1.1 Element-level subscription setup

1. Scene elements declare feature requirements via `registerFeatureRequirements` (`src/audio/audioElementMetadata.ts`).
2. When an element mounts or its track binding changes, `BaseSceneElement` (and hooks like `useAudioFeature`) call `syncElementSubscriptions` / `getFeatureData`.
3. `getFeatureData` (scene API) is the primary entry point:
    - Builds or normalises the requested descriptor (`createFeatureDescriptor`).
    - Acquires a `FeatureSubscriptionController` keyed to the element instance.
    - Normalises the track ID; if absent, the controller is reset and the call returns `null`.

### 1.2 Subscription aggregation & intent publication

1. `FeatureSubscriptionController` maintains three descriptor pools (`static`, `explicit`, `adHoc`) and the active track.
2. Any descriptor change or track switch triggers `flush()`, which:
    - Aggregates descriptors respecting priority and profile overrides.
    - Publishes the consolidated list via `publishAnalysisIntent` (see `src/audio/features/analysisIntents.ts`).
3. Intents lan

*[truncated — see source for full prompt]*