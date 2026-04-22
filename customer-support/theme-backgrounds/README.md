# Theme Backgrounds

> The theme system supports custom background textures and gradients through the `backgrounds` property in theme definitions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Theme Background System

The theme system supports custom background textures and gradients through the `backgrounds` property in theme definitions. This allows each theme to define its own visual treatment for content areas, sidebars, and UI chrome without modifying global CSS.

## Overview

Backgrounds are configured in `theme.ts` files and automatically applied when themes are switched. The system supports:

-   Content area backgrounds (base layer + overlay)
-   Sidebar backgrounds
-   Header and bottom nav gradients
-   Public image URLs or user-uploaded files via internal tokens
-   Per-layer opacity, repeat, and size controls

## Theme DSL

### ThemeBackgroundLayer

Defines a single background layer with the following properties:

```typescript
interface ThemeBackgroundLayer {
    image?: string | null; // URL or internal-file:// token
    color?: string; // Optional background color
    opacity?: number; // 0-1, clamped at runtime
    repeat?: 'repeat' | 'no-repeat' | 'repeat-x' | 'repeat-y';
    size?: string; // CSS size value (e.g., '150px', 'cover')
    fit?: 'cover' | 'contain'; // Convenience shorthand for size
}
```

### ThemeBackgrounds

Container for all background layers in a theme:

```typescript
interface ThemeBackgrounds {
    content?: {
        base?: ThemeBackgroundLayer; // Primary content background
        overlay?: ThemeBackgroundLayer; // Secondary overlay pattern
    };
    sidebar?: ThemeBackgroundLayer; // Sidebar background
    headerGradient?: ThemeBackgroundLayer; // Top chrome gradient
    bottomNavGradient?: ThemeBackgroundLayer; // Bottom chrome gradient
}
```

## Usage Example

### Retro Theme

```typescript
export default defineTheme({
    name: 'retro',
    displayName: 'Retro (Default)',
    // ...colors, overrides, etc.

    backgrounds: {
        content: {
            base: {
                image: '/bg-repeat.webp',
                opacity: 0.08,
                repeat: 'repeat',
                size: '150px',
        

*[truncated — see source for full prompt]*