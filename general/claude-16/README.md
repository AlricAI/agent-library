# CLAUDE

> ## What this is
A standalone web landing page for the **urordo** desktop app (Tauri + Rust + React, Windows file organiser). Lives in `landing/` insid

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLAUDE.md — urordo Landing Page

## What this is
A standalone web landing page for the **urordo** desktop app (Tauri + Rust + React, Windows file organiser). Lives in `landing/` inside the main repo. Deployed separately to **Cloudflare Pages**.

---

## Psychological Journey (the design law)
Every section answers a silent user question. Do not add persuasion — remove resistance.

| Section | Silent question | Goal |
|---|---|---|
| Nav | — | Orientation |
| Hero | "Is this for me?" | Attention: bold promise |
| Game Stage | "Do they understand my problem?" | Recognition: live demo |
| What is urordo | "What do I actually gain?" | Desire: concrete benefits |
| Features | "Can this really do that?" | Desire: proof via detail |
| How It Works | "Is it complicated?" | Simplicity: 3 steps |
| Who Is It For | "Am I the right person?" | Trust: personas |
| CTA | "What happens if I act?" | Action: frictionless |
| Footer | "Is this trustworthy?" | Trust: legal, GitHub |

---

## Tech Stack

| Concern | Choice |
|---|---|
| Framework | React 18 + TypeScript |
| Build | Vite 6 |
| Styling | Pure CSS (all custom, no framework) |
| Fonts | Google Fonts: Cormorant Garamond + DM Mono |
| Animations | Pure CSS keyframes + Intersection Observer + Canvas API |
| Deploy | Cloudflare Pages (static build) |

---

## Dev commands

```bash
cd landing
npm install      # first time only
npm run dev      # → http://localhost:5173
npm run build    # → dist/
npm run preview  # preview production build
npm run typecheck # TypeScript check, no emit
```

## Cloudflare Pages settings
- **Root directory**: `landing`
- **Build command**: `npm run build`
- **Output directory**: `dist`
- No environment variables required.

---

## Design System

### Colors (all via CSS custom properties — never hardcode hex)

| Token | Light | Dark | Usage |
|---|---|---|---|
| `--paper` | `#f8f5ef` | `#1a1710` | Page background |
| `--paper2` | `#f2ede4` | `#211e14` | Subtle sections |
| `--paper3` | `#ece5d8` | `

*[truncated — see source for full prompt]*