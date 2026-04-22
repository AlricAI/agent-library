# Css Selectors Implementation

> ## Overview

Successfully implemented a hybrid build-time CSS + runtime class system for the refined theme system, as outlined in the planning documen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CSS Selectors Implementation Summary

## Overview

Successfully implemented a hybrid build-time CSS + runtime class system for the refined theme system, as outlined in the planning documents.

## What Was Implemented

### 1. Type System Updates

**File:** `app/theme/_shared/types.ts`

- Added `CSSelectorConfig` interface with `style` and `class` properties
- Extended `ThemeDefinition` interface with `cssSelectors` field
- Extended `CompiledTheme` interface with `cssSelectors` field

### 2. Build-Time CSS Generator

**File:** `scripts/build-theme-css.ts`

- Converts `cssSelectors.style` properties to CSS files
- Generates `public/themes/{theme}.css` files
- Uses `[data-theme="name"] selector` for scoping
- Converts camelCase to kebab-case for CSS properties
- CLI-runnable via `bun run theme:build-css`

### 3. Runtime Class Application

**File:** `app/theme/_shared/css-selector-runtime.ts`

Functions:
- `applyThemeClasses()` - Applies Tailwind classes to matching elements
- `removeThemeClasses()` - Removes classes when switching themes
- `loadThemeCSS()` - Loads theme CSS file dynamically
- `unloadThemeCSS()` - Removes theme CSS file

Features:
- WeakMap-based caching to avoid duplicate class application
- Graceful error handling for invalid selectors
- No memory leaks (WeakMap auto-cleans with GC)

### 4. Theme Plugin Integration

**File:** `app/plugins/01.theme.client.ts`

Updates:
- Imports CSS selector runtime functions
- Passes `cssSelectors` to compiled theme
- Loads CSS files on theme switch
- Applies/removes classes on theme change
- Sets `data-theme` attribute on `<html>`
- Auto-applies classes on page navigation via `page:finish` hook

### 5. Composable for Lazy Components

**File:** `app/composables/core/useThemeClasses.ts`

- `useThemeClasses()` composable for lazy-loaded components
- Automatically applies theme classes on mount
- Ensures theme is loaded before applying

### 6. Documentation

**File:** `docs/css-selectors.md`

Comprehensive guide coverin

*[truncated — see source for full prompt]*