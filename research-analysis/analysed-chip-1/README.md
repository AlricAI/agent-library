# Analysed Chip 1

> ## UI Surfaces

-   Track lanes render the chip inside each audio clip using `featureStatusLabel`, mapping store states to colors and text in [src/wor

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Audio Analysis Chip States

## UI Surfaces

-   Track lanes render the chip inside each audio clip using `featureStatusLabel`, mapping store states to colors and text in [src/workspace/panels/timeline/TrackLanes.tsx#L286-L339](src/workspace/panels/timeline/TrackLanes.tsx#L286-L339).
-   Scene analysis diagnostics mirror the same labels inside the cache inspector tab via `getStatusMeta` in [src/workspace/layout/SceneAnalysisCachesTab.tsx#L27-L57](src/workspace/layout/SceneAnalysisCachesTab.tsx#L27-L57).

## State Matrix

| Store state     | Chip label                      | Primary setter                       | Trigger summary                                                                                                                                                                                                                                                                                                                                                                       |
| --------------- | ------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| undefined entry | Not analysed                    | Track UI default                     | When no `audioFeatureCacheStatus[sourceId]` exists (e.g., brand-new audio track or cache entry deleted) the UI falls through to the default label, so users still see "Not analysed" even though no request ever ran [src/workspace/panels/timeline/TrackLanes.tsx#L286-L339](src/workspace/panels/timeline/TrackLanes.tsx#L286-L339).                                                |
| idle            | Not analysed                    | `ingestAudi

*[truncated — see source for full prompt]*