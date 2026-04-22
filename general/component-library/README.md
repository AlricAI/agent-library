# Component Library

> ## Overview

This document defines the reusable UI components for the YouAndINotAI platform. All components are designed with mobile-first principles,

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# YouAndINotAI Component Library

## Overview

This document defines the reusable UI components for the YouAndINotAI platform. All components are designed with mobile-first principles, accessibility compliance, and trust-building in mind.

## Core Components

### Buttons

#### Primary Button

```jsx
<Button variant="primary" size="md" disabled={false} onClick={handleClick}>
  Label
</Button>
```

**Props:**

- `variant`: "primary" | "secondary" | "danger" | "success"
- `size`: "sm" | "md" | "lg"
- `disabled`: Boolean
- `onClick`: Function
- `children`: Node

**Design Tokens Used:**

- Background: `--brand-primary` for primary variant
- Text: `--text-inverse`
- Padding: `--spacing-button-padding-v` vertical, `--spacing-button-padding-h` horizontal
- Border radius: `--border-radius-md`
- Focus ring: `--focus-ring-color`

#### Secondary Button

```jsx
<Button variant="secondary" size="md" disabled={false} onClick={handleClick}>
  Label
</Button>
```

**Props:** Same as Primary Button

**Design Tokens Used:**

- Background: `--bg-secondary`
- Border: `--border-width-thin` solid `--text-secondary`
- Text: `--text-primary`
- Padding: `--spacing-button-padding-v` vertical, `--spacing-button-padding-h` horizontal
- Border radius: `--border-radius-md`

#### Icon Button

```jsx
<IconButton icon="heart" variant="primary" size="md" disabled={false} onClick={handleClick} />
```

**Props:**

- `icon`: String (icon name)
- `variant`: "primary" | "secondary" | "danger" | "success"
- `size`: "sm" | "md" | "lg"
- `disabled`: Boolean
- `onClick`: Function

**Design Tokens Used:**

- Size: Square based on `--spacing-8` for md size
- Background: `--brand-primary` for primary variant
- Border radius: `--border-radius-full`

### Inputs

#### Text Input

```jsx
<TextInput label="Label" placeholder="Placeholder" error="" disabled={false} onChange={handleChange} value={value} />
```

**Props:**

- `label`: String
- `placeholder`: String
- `error`: String (error message)
- `disabled`: Boolean

*[truncated — see source for full prompt]*