# Cache System Strengths Limitations

> ## Strengths

- **Single source of truth for analyzed data.** The cache pipeline analyzes audio buffers, aligns frames to the tempo map, and exposes c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cache System Strengths and Limitations

## Strengths

- **Single source of truth for analyzed data.** The cache pipeline analyzes audio buffers, aligns frames to the tempo map, and exposes consistent feature tracks for every scene element, so renderers pull from deterministic data rather than recomputing per frame.【F:docs/audio/audio-cache-system.md†L5-L24】
- **Shared ownership and deduplication.** Timeline state persists cache payloads, tracks status, and deduplicates descriptor requests through the analysis intent bus, eliminating redundant analyses when multiple surfaces need the same features.【F:docs/audio/audio-cache-system.md†L41-L75】【F:docs/audio/audio-cache-system.md†L101-L133】
- **Separation of analysis and presentation.** Feature descriptors describe analysis identity while sampling options tune smoothing or interpolation at render time, letting elements experiment visually without fragmenting caches.【F:docs/audio/audio-cache-system.md†L47-L120】【F:docs/audio/concepts.md†L9-L28】
- **Channel-aware routing.** Channel aliases stored with each feature track surface semantic labels
  such as `Left`, `Right`, `Mid`, or `Side`, enabling runtime helpers to pick the appropriate channel
  after sampling without fragmenting descriptors.【F:docs/audio/audio-cache-system.md†L77-L128】【F:src/audio/features/channelResolution.ts†L1-L104】
- **Tempo-aligned sampling utilities.** `getFeatureData` and `sampleFeatureFrame` convert playback time to ticks, fetch tempo-aware frames, cache recent samples, and record diagnostics automatically, so element code stays focused on presentation logic.【F:src/audio/features/sceneApi.ts†L197-L278】【F:src/core/scene/elements/audioFeatureUtils.ts†L21-L177】
- **Versioned, profile-aware payloads.** Feature tracks retain calculator ids, versions, analysis parameters, and optional profiles, enabling cache reuse across exports while still invalidating when algorithms change.【F:docs/audio/audio-cache-system.md†L77-L166】

## Limitations

- **Reanalysi

*[truncated — see source for full prompt]*