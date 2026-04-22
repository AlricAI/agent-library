# UX/UI Workflow & Design System

> description: Use when working on UI/UX tasks, user experience design, interface components, and user journey optimization - provides comprehensive UX workflow with design systems integration. alwaysApply: false UX/UI Workflow & Design System

## Tags
`react`

## System Prompt
---
description: Use when working on UI/UX tasks, user experience design, interface components, and user journey optimization - provides comprehensive UX workflow with design systems integration.
alwaysApply: false
---
# UX/UI Workflow & Design System

This rule provides comprehensive guidance for UI/UX development in Igniter.js + Next.js + Shadcn UI projects, ensuring consistent design systems, user experience optimization, and seamless integration with existing workflows.

## 1. Design System Integration Protocol

### 1.1 Mandatory Design Token Usage
**CRITICAL**: Always use design tokens from `globals.css` instead of hardcoded values. This ensures consistency across the application and proper theme support.

**Available Design Tokens:**
```css
/* Background & Surface */
--background: oklch(1 0 0);                    /* Main background */
--card: oklch(0.21 0.006 285.885);           /* Card backgrounds */
--popover: oklch(0.21 0.006 285.885);        /* Popover backgrounds */
--muted: oklch(0.967 0.001 286.375);         /* Muted backgrounds */

/* Foreground & Text */
--foreground: oklch(0.141 0.005 285.823);    /* Primary text */
--card-foreground: oklch(0.985 0 0);         /* Card text */
--muted-foreground: oklch(0.552 0.016 285.938); /* Muted text */

/* Interactive Elements */
--primary: oklch(0.21 0.006 285.885);        /* Primary actions */
--primary-foreground: oklch(0.985 0 0);      /* Primary text */
--secondary: oklch(0.967 0.001 286.375);     /* Secondary actions */
--accent: oklch(0.967 0.001 286.375);        /* Accent elements */

/* Interactive States */
--ring: oklch(0.705 0.015 286.067);          /* Focus rings */
--border: oklch(0.92 0.004 286.32);          /* Borders */
--input: oklch(0.92 0.004 286.32);           /* Input backgrounds */

/* Sidebar System */
--sidebar: oklch(0.985 0 0);                 /* Sidebar background */
--sidebar-foreground: oklch(0.141 0.005 285.823); /* Sidebar text */
--sidebar-primary: oklch(0.488 0.243 264.376); /* S

*[truncated — see source for full prompt]*