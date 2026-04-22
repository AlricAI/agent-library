# Todos

> [← Back to Index](./index.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tech Invoice Forge - Implementation Todos

[← Back to Index](./index.md) | [Master Plan](./master-plan.md)

---

## Overview

This document tracks all implementation tasks for Tech Invoice Forge. Tasks are organized by phase and component. Mark items as `[x]` when complete, `[/]` when in progress.

---

## Phase 0: Project Setup

### Initial Setup

- [ ] Create SvelteKit project with `bunx sv create tech-invoice-forge`
- [ ] Initialize with TypeScript, Prettier, ESLint
- [ ] Add Tailwind CSS v4 with `bunx sv add tailwindcss`
- [ ] Add shadcn-svelte with `bunx sv add shadcn-svelte`
- [ ] Configure static adapter in `svelte.config.js`
- [ ] Set up path aliases in `svelte.config.js`

### Configure Tailwind

- [ ] Create custom color palette in `src/routes/layout.css`
- [ ] Add brand colors (indigo, emerald, amber)
- [ ] Add surface colors (slate-800, slate-900)
- [ ] Configure dark mode as default
- [ ] Add tailwindcss-animate plugin

### Install Core Dependencies

- [x] Configure svelte-idb compatibility adapter
- [ ] Install pdfmake for PDF generation
- [ ] Install valibot for validation
- [ ] Install @internationalized/date
- [ ] Install lucide-svelte icons

### Add shadcn Components

- [ ] Add Button component
- [ ] Add Input component
- [ ] Add Textarea component
- [ ] Add Select component
- [ ] Add Popover component
- [ ] Add Calendar component
- [ ] Add Card component
- [ ] Add Dialog component
- [ ] Add Tabs component
- [ ] Add Table component
- [ ] Add Tooltip component
- [ ] Add Badge component
- [ ] Add Separator component
- [ ] Add ScrollArea component
- [ ] Add Sheet component
- [ ] Add Alert component

### Create Base Layout

- [ ] Create root layout with dark theme
- [x] **Configure `ssr: false` in `+layout.ts`** (required for IndexedDB)
- [ ] Add Inter and JetBrains Mono fonts
- [ ] Create Header component
- [ ] Create responsive navigation
- [ ] Add theme toggle (future light mode)

---

## Phase 1: Core MVP

### Database Layer

- [x] Create `$lib/db

*[truncated — see source for full prompt]*