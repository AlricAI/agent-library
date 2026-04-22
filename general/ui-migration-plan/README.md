# UI MIGRATION PLAN

> ## Overview

Replace the React/Ink-based UI (`ui.tsx`) with a raw ANSI terminal UI based on the proven `uiexperiment/` approach. This removes the Ink 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Jambot UI Migration: Ink → Raw ANSI

## Overview

Replace the React/Ink-based UI (`ui.tsx`) with a raw ANSI terminal UI based on the proven `uiexperiment/` approach. This removes the Ink framework entirely while preserving all functionality.

## Goals

1. **Keep all features**: messages, scrolling, input, autocomplete, status bar, menus
2. **Improve reliability**: no more Ink rendering quirks
3. **Enable native scrollback**: primary buffer with scroll regions
4. **Support resize/reflow**: content reflows on terminal resize

## Architecture

### Before (Ink)
```
ui.tsx (React components)
    ↓
Ink render() → terminal
```

### After (Raw ANSI)
```
terminal-ui.ts (class-based)
    ↓
ANSI escape codes → terminal
```

## File Changes

| Action | File | Notes |
|--------|------|-------|
| DELETE | `ui.tsx` | After migration complete |
| CREATE | `terminal-ui.ts` | New main UI (port from uiexperiment) |
| MODIFY | `jambot.js` | Update to use new UI class |
| MODIFY | `package.json` | Remove ink, ink-text-input, react |
| MODIFY | `build.js` | Update entry point |

## Dependencies

### Remove
```
- ink
- ink-text-input
- react
```

### Keep
```
- wrap-ansi (text wrapping)
- string-width (ANSI-aware width)
- chalk (colors - optional, can use raw ANSI)
```

### Add (maybe)
```
- None required (raw ANSI needs no deps)
```

---

## Phase 1: Core Terminal UI Class

**Goal**: Basic UI shell that can display messages and accept input.

### 1.1 Create `terminal-ui.ts`

Port from `uiexperiment/src/index.ts` with these additions:

```typescript
class TerminalUI {
  // From uiexperiment
  private rows: number;
  private cols: number;
  private inputBuffer: string;
  private contentHistory: string[];

  // New for Jambot
  private messages: Message[];
  private scrollOffset: number;
  private isProcessing: boolean;
  private session: Session;
  private project: Project | null;

  // Callbacks for agent loop
  public onSubmit: (input: string) => Promise<void>;
}
```

### 1.2 Message R

*[truncated — see source for full prompt]*