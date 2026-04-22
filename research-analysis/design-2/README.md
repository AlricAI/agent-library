# Design

> ## 1. Intro
- **Purpose:** Describe the client-side architecture of bg-trainer: how screens, hooks, engines, and data combine to deliver quiz sessions

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# SDS

## 1. Intro
- **Purpose:** Describe the client-side architecture of bg-trainer: how screens, hooks, engines, and data combine to deliver quiz sessions and analytics.
- **Rel to SRS:** Implements FR-MENU, FR-GAME-SESSION, FR-SCORING, FR-ENGINES, FR-MATCH, FR-ODD, FR-PARADIGM, FR-REACTION, FR-HISTORY, FR-ANALYTICS, FR-RESULTS, FR-NAV, FR-LESSONS, FR-ROUND, FR-MASTERY, FR-SCHED, FR-TYPE, FR-FEEDBACK-RULE, FR-IOS-SHELL.

## 2. Arch
- **Diagram:**
  ```mermaid
  flowchart LR
    User((User)) --> App[App.tsx]
    App -->|screen=lessons| Lessons[LessonsScreen]
    App -->|screen=lesson| Lesson[LessonScreen]
    App -->|screen=game| Engine[Engine*]
    App -->|screen=results| Results[ResultsScreen]
    App -->|screen=analytics| Analytics[AnalyticsScreen]
    Engine --> useGame[(useGame hook)]
    Engine -.timed.-> useTimer[(useTimer hook)]
    App --> History[(localStorage\n bg-trainer-v3)]
    App --> Mastery[(localStorage\n bg-trainer-mastery-v1)]
    Analytics --> History
    Lessons --> Mastery
    Lesson --> Mastery
    App --> Data[(data/index.ts\n + lesson1.ts + lesson2.ts\n + lesson3.ts + lesson4.ts)]
    App --> Lessons2[(data/lessons.ts)]
    App --> Slice[(utils/sliceData)]
  ```
- **Subsystems:**
  - **Shell (`App.tsx`):** screen router + session lifecycle + history persistence.
  - **Engines (`components/engines/*`):** one React component per `EngineType`. Consumes `useGame`.
  - **State hooks (`hooks/*`):** `useGame` (scoring, advance, reaction), `useTimer` (countdown for timed mode).
  - **Data layer (`data/index.ts` + `data/lesson1.ts` + `data/lesson2.ts` + `data/lesson3.ts` + `data/lesson4.ts`):** exercises split per-lesson; `index.ts` is composition root — imports datasets from lesson files, re-exports via `export *`, defines `CATEGORIES` + `ALL_MODES`. Shared labels (`LABEL_M/F/N/PL`) live in `lesson1.ts` and are imported by later lessons. L10n fields stored as `Localized<string>`. Translation pairs inside `DataItem.q` use convention `"<ru> / <uk>"

*[truncated — see source for full prompt]*