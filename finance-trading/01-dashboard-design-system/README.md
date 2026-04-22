# 01 Dashboard Design System

> ## Context

You are working on `crypto-vision`, a cryptocurrency intelligence platform. The dashboard lives in `apps/dashboard/` (Next.js 15, Tailwind

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 01 — Dashboard Core Layout & Design System

## Context

You are working on `crypto-vision`, a cryptocurrency intelligence platform. The dashboard lives in `apps/dashboard/` (Next.js 15, Tailwind CSS, App Router). The current UI is a CoinGecko/CoinMarketCap clone that needs a complete redesign into a professional, dark-themed trading platform UI.

**Keep all existing code** — API integrations, lib modules, SDK, CLI, MCP, services, providers. Only redesign the visual layer.

## Existing Structure

- `apps/dashboard/src/app/layout.tsx` — Root layout
- `apps/dashboard/src/app/globals.css` — Global styles with CSS variables (design tokens already defined)
- `apps/dashboard/src/components/Header.tsx` — Navigation header
- `apps/dashboard/src/components/Footer.tsx` — Footer
- `apps/dashboard/src/components/ui/` — Base UI components
- `apps/dashboard/tailwind.config.js` — Tailwind config

## Task

### 1. Create a New Design System

Replace the CoinGecko aesthetic with a professional trading terminal / Bloomberg-style dark theme:

**Color Palette:**
- Background: `#0a0a0f` (near-black), `#12121a` (card surface), `#1a1a2e` (elevated surface)
- Accent: `#00d4aa` (primary teal/green), `#7b61ff` (secondary purple)
- Gain: `#00d68f`, Loss: `#ff3d71`, Warning: `#ffaa00`
- Text: `#e4e4e7` (primary), `#a1a1aa` (secondary), `#52525b` (muted)
- Border: `rgba(255,255,255,0.06)`

**Typography:**
- Font: Inter for UI, JetBrains Mono for numbers/prices
- Sizes: Tight, information-dense layout

**Components needed:**
- Glass-morphism cards with subtle borders
- Animated number transitions for prices
- Sparkline mini-charts
- Status indicators (pulsing dots)
- Gradient accent borders on active elements
- Skeleton loaders with shimmer effect

### 2. Redesign the Root Layout (`layout.tsx`)

Create a new layout with:
- **Left sidebar** (collapsible, 64px collapsed / 240px expanded):
  - Logo at top
  - Navigation groups: Markets, Trading, Swarm, Portfolio, Research, Admin
  - Active i

*[truncated — see source for full prompt]*