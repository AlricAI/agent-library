# Architecture

> ## Three-Panel Layout

The app fills 100dvh with three equal vertical panels. Each panel is `flex: 0 0 33.333%` inside a column flexbox on `.app`.

``

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Architecture Spec

## Three-Panel Layout

The app fills 100dvh with three equal vertical panels. Each panel is `flex: 0 0 33.333%` inside a column flexbox on `.app`.

```
┌─────────────────────────────────┐
│  WordDisplay  (top 1/3)         │  RSVP focal point — one word at a time
├─────────────────────────────────┤
│  PDFPageView / TextPreview      │  Page canvas (PDF) or scrolling text (EPUB)
│  (middle 1/3)                   │
├─────────────────────────────────┤
│  Bottom panel  (bottom 1/3)     │
│  ├─ PDFUpload (file picker)     │
│  ├─ Controls row 1 (transport)  │
│  └─ Controls row 2 (WPM inputs) │
└─────────────────────────────────┘
```

The middle panel is **always rendered** — hiding it collapses the layout.
- PDF loaded → `PDFPageView` (canvas preview of current page)
- EPUB loaded → `TextPreview` (scrolling word context)
- Nothing loaded → `TextPreview` empty state

The **TOC overlay** (`TocDrawer`) is a full-screen `position: fixed` layer rendered outside the three-panel flow, mounted conditionally in `App.tsx`.

## Component Tree

```
App
├── WordDisplay          — ORP word rendering
├── PDFPageView          — PDF canvas + word highlight box (PDF only)
├── TextPreview          — Windowed word list with active highlight (EPUB / no-PDF)
├── div.bottom-panel
│   ├── PDFUpload        — Drag-and-drop / click file picker
│   └── Controls         — Transport buttons, progress bar, WPM inputs
└── TocDrawer (conditional) — Full-screen chapter navigator
```

## State — App.tsx

All playback state lives in `App.tsx`. Child components receive only what they need.

| State | Type | Purpose |
|---|---|---|
| `words` | `WordToken[]` | Extracted words with position metadata |
| `wordIndex` | `number` | Current word being displayed |
| `playState` | `'idle'\|'playing'\|'paused'` | Playback mode |
| `minWpm` / `maxWpm` | `number` | Speed ramp bounds |
| `currentWpm` | `number` | Rolling 10s average WPM (display only) |
| `pdfDoc` | `PDFDocumentProxy\|null` | PDF docu

*[truncated — see source for full prompt]*