# Design System Implementation Guide

> ## Overview

This guide provides detailed implementation instructions for the YouAndINotAI design system. It covers setup, component usage, and best p

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# YouAndINotAI Design System Implementation Guide

## Overview

This guide provides detailed implementation instructions for the YouAndINotAI design system. It covers setup, component usage, and best practices for developers integrating the design system into the React 19 codebase.

## System Setup

### Installation

The design system is integrated directly into the React codebase as CSS custom properties and React components. No additional installation is required beyond the standard project dependencies.

### CSS Custom Properties

All design tokens are implemented as CSS custom properties in the global stylesheet. These properties are defined in `:root` and scoped variants for dark mode.

```css
:root {
  /* Brand Colors */
  --brand-primary: #ff4f00;
  --brand-secondary: #111111;
  --brand-accent: #fff4ef;

  /* Typography */
  --font-family-base: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  --font-size-base: 1rem;

  /* Spacing */
  --spacing-4: 1rem;
  --spacing-6: 1.5rem;

  /* And all other tokens from design-system-tokens.md */
}
```

## Component Implementation Guide

### Buttons

#### Primary Button Implementation

```jsx
import React from 'react';
import './Button.css';

const Button = ({ variant = 'primary', size = 'md', disabled = false, children, ...props }) => {
  const className = `btn btn-${variant} btn-${size} ${disabled ? 'btn-disabled' : ''}`;

  return (
    <button className={className} disabled={disabled} {...props}>
      {children}
    </button>
  );
};

export default Button;
```

```css
/* Button.css */
.btn {
  font-family: var(--font-family-base);
  font-weight: var(--font-weight-semibold);
  border: none;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  transition: all var(--transition-duration-normal) var(--transition-easing);
}

.btn:focus {
  outline: var(--focus-ring-width) solid var(--focus-ring-color);
  outline-offset: var(--focus-ring-offset

*[truncated — see source for full prompt]*