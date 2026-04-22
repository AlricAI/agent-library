# UX UPGRADE PLAN

> Tracks implementation state for the 20-initiative UI/UX upgrade sequenced in four waves.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# UX Upgrade Plan — Rollout Notes
Tracks implementation state for the 20-initiative UI/UX upgrade sequenced in four waves. This document is the map from "shipped primitive" to "fully adopted behavior" across the app. Keep it current as consumers migrate.
## Definitions
- **Shipped primitive**: exists under `src/lib`, `src/components`, or `src/hooks`. Typechecks, has tests where applicable, and can be imported.
- **Adopted**: a real user-facing surface imports the primitive, so an end user experiences the change. Anything not explicitly listed as adopted should be treated as library-only.
## Adoption Matrix (source of truth)
### Adopted end-to-end
| Primitive | Adoption site | User-visible effect |
| --- | --- | --- |
| `OnboardingTour` | `AppShell` (root mount) | First-run walkthrough appears automatically; dismisses once per user via `localStorage['onboarding:completed-v1']`. |
| `BasedOnPanel` | `AIMessage` | Every Ask AI answer with curated links shows a collapsible "Based on" panel exposing link list + response source / model. |
| `useDensityPreference` + `data-density` | `AppShell` root attribute, `DataTable` default via `readDensitySync()`, Settings toggle | User selects Compact / Comfortable; tables render at matching row height globally. |
| `copyText()` | `LinkQuickActions` | Every Google Doc / Live URL / Canva link copy surfaces a semantic toast like "Copied Google Doc URL". |
| `EmptyState` (via `DataPageEmptyState`) | Dashboard, My Tasks, Blogs, Social Posts, Ideas list empty states | One consistent empty-state look; backed by `UI_VOCAB.emptyStates` where applicable. |
| Sidebar auto-collapse | `useSidebarState` | Below 1400px auto-collapses the first time; explicit user toggle wins afterwards. |
| `NextActionCell` | `/tasks` Next Action column | Verb-first cell ("Submit Draft", "Publish Blog", "Waiting on Jane") replaces raw status pill. |
| `parseRecordDeepLink()` | `/social-posts` list | `?record=blog:<id>` or `?record=social:<id>` routes to the match

*[truncated — see source for full prompt]*