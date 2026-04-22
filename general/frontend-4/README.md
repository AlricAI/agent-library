# Frontend

> React 19 + Zustand 5 + Vite 6 SPA.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Frontend

React 19 + Zustand 5 + Vite 6 SPA. Python serves the built bundle as static
files — no Node.js in production.

> Parent doc: [architecture.md](./architecture.md)

---

## Directory Layout

```
frontend/
├── AGENTS.md               # frontend-specific agent rules (read first)
├── package.json
├── tsconfig.json
├── vite.config.ts          # proxies /api/*, /events, /mcp/* to Python in dev
├── index.html              # Vite entry point
├── src/
│   ├── main.tsx            # mounts <App /> into #root; imports global CSS
│   ├── App.tsx             # top-level layout; owns SSE connection lifecycle
│   ├── utils.ts            # formatTokens, formatSize, normalizeOptions
│   ├── store/
│   │   ├── index.ts        # single Zustand store (the app-db equivalent)
│   │   └── selectors.ts    # derived state computed from store slices
│   ├── sse/
│   │   └── connect.ts      # EventSource wrapper: always-snapshot catch-up + JSON Patch
│   ├── api/
│   │   └── client.ts       # typed fetch wrappers for POST/PUT endpoints
│   ├── components/
│   │   ├── AGENTS.md       # component development rules (read when building components)
│   │   ├── atoms/          # StatusDot, Badge, Button, SectionLabel, LogoMark, ProgressSegment
│   │   ├── molecules/      # ProseCard, ThinkingBlock, ToolCallRow, FeedbackInput, etc.
│   │   ├── organisms/      # HeaderBar, ScoutBar, ArtifactsSidebar, ElicitationPanel, NewRunForm
│   │   ├── Md.tsx          # shared markdown renderer (ReactMarkdown + remark-gfm)
│   │   ├── Notification.tsx # toast notification system
│   │   └── SettingsOverlay.tsx # settings modal (not yet redesigned)
│   ├── hooks/
│   │   ├── useElapsed.ts   # elapsed time hook for agent start times
│   │   └── useAutoScroll.ts # sticky-scroll for content stream
│   └── styles/
│       ├── variables.css   # design tokens (PROTECTED — see frontend/AGENTS.md)
│       ├── app-shell.css   # page frame layout (.app-root, .workflow-grid)
│       ├── markdown.css    # rendered 

*[truncated — see source for full prompt]*