# Import Export Consistency 1

> ## Status
Open for review

## Context
The codebase mixes CommonJS-inspired default exports with ES module named exports, and switches between path ali

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Import/Export Consistency Plan

## Status
Open for review

## Context
The codebase mixes CommonJS-inspired default exports with ES module named exports, and switches between path alias imports (e.g. `@export/...`) and relative paths within the same feature areas. The `src/AGENTS.md` guidelines prefer named exports and alias usage for intra-project modules, but multiple files currently diverge from that expectation.

Representative examples:
- `src/export/export-clock.ts` defines both a named `ExportClock` class and a default export of the same class, encouraging inconsistent import styles across consumers.【F:src/export/export-clock.ts†L6-L53】【F:src/export/export-clock.ts†L55-L56】
- Callers alternate between alias and relative imports for the same module: `video-exporter.ts` imports `ExportClock` via `@export/export-clock`, while `av-exporter.ts` and tests rely on `./export-clock` or `../export-clock` relative paths.【F:src/export/video-exporter.ts†L6-L9】【F:src/export/av-exporter.ts†L22-L24】【F:src/export/__tests__/video-export-timestamps.test.ts†L1-L18】
- Some utilities expose both aggregated named exports and a `default` alias (e.g., `noteQueryApi`), leading to ambiguity on the preferred import shape for new call sites.【F:src/core/timing/note-query.ts†L1-L99】【F:src/core/timing/note-query.ts†L160-L170】
- Within the note animation suite, import ordering and alias usage are inconsistent (`template.ts` mixes alias imports with locals in varying order, and `press.ts` keeps inline comments and unsorted alias references).【F:src/animation/note-animations/template.ts†L1-L31】【F:src/animation/note-animations/press.ts†L1-L38】

These inconsistencies complicate discoverability, hamper tree-shaking expectations, and raise onboarding questions around the “correct” pattern to follow.

## Goals
- Align every module with a single export convention (prefer named exports, no redundant default exports) to match project guidance.
- Establish deterministic rules for when to use path alias

*[truncated — see source for full prompt]*