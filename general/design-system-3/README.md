# DESIGN SYSTEM

> ## Overview

The MyMemory design system is built on **HeroUI Native** + **Uniwind (Tailwind CSS for React Native)** with a custom Material Design 3-in

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MyMemory Design System

## Overview

The MyMemory design system is built on **HeroUI Native** + **Uniwind (Tailwind CSS for React Native)** with a custom Material Design 3-inspired color palette derived from the Stitch design reference.

**Stack:**
- **HeroUI Native** — component library (Card, Button, TextField, ListGroup, Toast, etc.)
- **Uniwind** — Tailwind CSS v4 runtime for React Native
- **Tailwind Variants** — component variant styling via `tv()`
- **Material Icons** — `@expo/vector-icons/MaterialIcons`

---

## Color System

Colors are defined as CSS variables in `src/global.css` using `@layer theme` with `@variant light` / `@variant dark` blocks. They override HeroUI Native's default theme.

### Semantic Color Tokens

Hex values are the current mirrors in `apps/mobile/src/theme/tokens.ts`; the canonical oklch definitions live in `apps/mobile/src/global.css`.

| Token | Light | Dark | Usage |
|-------|-------|------|-------|
| `background` | `#F9F9F9` | `#212529` | Page/screen background |
| `foreground` | `#1A1C1C` | `#F8F9FA` | Primary text |
| `muted` | `#73787B` | `#ADB5BD` | Secondary/hint text, icons |
| `surface` | `#FFFFFF` | `#495057` | Cards, elevated containers |
| `surface-secondary` | `#F3F3F3` | `#343A40` | Slightly tinted surface |
| `surface-tertiary` | `#EEEEEE` | `#6C757D` | More tinted surface |
| `accent` | `#334550` | `#9BA7AF` | Brand/interactive color |
| `accent-foreground` | `#FFFFFF` | `#212529` | Text on accent |
| `default` | `#E2E2E2` | `#343A40` | Neutral chips/badges |
| `default-foreground` | `#1A1C1C` | `#F8F9FA` | Text on default |
| `border` | `#C3C7CB` | `#6C757D` | Dividers, borders |
| `field-background` | `#FFFFFF` | `#343A40` | Input background |
| `field-foreground` | `#1A1C1C` | `#F8F9FA` | Input text |
| `field-placeholder` | `#73787B` | `#ADB5BD` | Input placeholder |
| `field-border` | `#C3C7CB` | `#495057` | Input border |
| `overlay` | `#FFFFFF` | `#343A40` | Dialog / popover background |
| `danger` | `#BA1A1

*[truncated — see source for full prompt]*