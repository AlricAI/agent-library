# Requirements

> ## 1. Intro
- **Desc:** bg-trainer — browser-based gamified grammar trainer for Bulgarian A0 learners. UI in Russian or Ukrainian (user-selectable). S

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# SRS

## 1. Intro
- **Desc:** bg-trainer — browser-based gamified grammar trainer for Bulgarian A0 learners. UI in Russian or Ukrainian (user-selectable). Single-page React app hosted on GitHub Pages.
- **Def/Abbr:** SPA = Single Page App. Engine = interaction component for one quiz type. Mode = one drill config (data + engine). Category = group of related modes. Session = one playthrough of N questions (N = `SESSION_SIZE_BY_PACE[pace]`). Lesson = textbook unit grouping a curated list of modes. Pace = user-selected session length (`quick`/`standard`/`deep`). Round = 3 consecutive N-question games from one lesson (N = pace size).

## 2. General
- **Context:** Self-study tool for East-Slavic speakers (RU/UK) at A0. No accounts, no backend. All state is client-side. Shipped as web (GitHub Pages) and native iOS (Capacitor WKWebView shell).
- **Assumptions/Constraints:**
  - Modern evergreen browser with `localStorage` and ES2020+.
  - Mobile-first, max-width `md`, portrait-friendly.
  - Static hosting for web (GitHub Pages at base `/bg-trainer/`); iOS build uses relative base `./`.
  - iOS deployment target 15.0+, Bundle ID `dev.korchasa.bgtrainer`, Capacitor 8.
  - No server, no analytics backend.
  - i18n: 2 locales (`ru`, `uk`), client-side only, no external i18n library.

## 3. Functional Reqs

### 3.1 FR-MENU
- **Desc:** Entry screen = list of lessons. Lessons carry a curated `modeIds` list. Available lessons open a per-lesson screen; upcoming lessons shown disabled with "Скоро" label.
- **Scenario:** User opens app → sees lessons list → taps available lesson → lesson screen with round button + grid of lesson's games → taps a game → game starts.
- **Acceptance:**
  - [x] Lessons list rendered with two sections (available / upcoming). Evidence: `src/components/screens/LessonsScreen.tsx:16-62`, `src/data/lessons.ts`
  - [x] Only `available=true` lessons are tappable. Evidence: `src/App.tsx:89-94`, `src/components/screens/LessonsScreen.tsx:35-52`
  - [x] Lesson scree

*[truncated — see source for full prompt]*