# Generator Workflow

> ## Overview

This workflow ensures all generated components are production-ready, fully tested, and properly integrated with the design system before 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Component Generator Workflow

## Overview

This workflow ensures all generated components are production-ready, fully tested, and properly integrated with the design system before being saved to the generator.

## Process Workflow

```
┌─────────────┐
│   Build     │ → Create component with design system tokens
└─────────────┘
       ↓
┌─────────────┐
│    Test     │ → Write comprehensive unit tests
└─────────────┘
       ↓
┌─────────────┐
│  Storybook  │ → Create interactive stories with variants
└─────────────┘
       ↓
┌─────────────┐
│ Smoke Test  │ → Verify in Storybook UI (http://localhost:6006)
└─────────────┘
       ↓
┌─────────────┐
│   Clear     │ → Remove example components from ui-components
└─────────────┘
       ↓
┌─────────────┐
│    Save     │ → Save templates to generator with atomic commit
└─────────────┘
```

## Detailed Steps

### 1. Build Component

**Requirements:**
- Use design system tokens (colors, spacing, typography)
- Support dark/light mode automatically
- Fully typed with TypeScript
- Accessible (WCAG 2.1 AA)
- Responsive design

**File Structure:**
```
packages/ui-components/src/components/
├── ComponentName.tsx          # Main component
├── ComponentName.test.tsx     # Unit tests
└── ComponentName.stories.tsx  # Storybook stories
```

**Component Template:**
```tsx
import { Card, Text, Button } from '@bg-kit/design-system';
import { spacing, colors } from '@bg-kit/design-system/tokens';
import { type ReactNode } from 'react';

export interface ComponentNameProps {
  // Props with proper documentation
  title: string;
  description?: string;
  variant?: 'primary' | 'success' | 'warning' | 'error';
}

/**
 * ComponentName - Brief description
 *
 * Detailed description of what this component does and when to use it.
 *
 * @example
 * ```tsx
 * <ComponentName title="Example" variant="primary" />
 * ```
 */
export function ComponentName({
  title,
  description,
  variant = 'primary',
}: ComponentNameProps) {
  return (
    <Card>
      

*[truncated — see source for full prompt]*