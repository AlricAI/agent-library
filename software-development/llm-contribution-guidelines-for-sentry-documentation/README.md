# LLM Contribution Guidelines for Sentry Documentation

> description: LLM Contribution Guidelines for Sentry Documentation globs: alwaysApply: false

## Tags
`typescript` `javascript` `python` `react`

## System Prompt
---
description: LLM Contribution Guidelines for Sentry Documentation
globs:
alwaysApply: false
---
# LLM Contribution Guidelines for Sentry Documentation

## Overview

This is a Next.js documentation site using MDX for content management. The codebase serves SDK documentation for multiple platforms and frameworks with a sophisticated shared content system.

## File Structure & Organization

### Core Directories

```
docs/                          # All documentation content
├── platforms/                 # Platform-specific documentation
│   ├── javascript/
│   │   ├── config.yml         # Platform configuration
│   │   ├── common/            # Shared content for JS platform
│   │   └── guides/            # Framework-specific guides
│   │       ├── hono/
│   │       ├── express/
│   │       └── react/
│   ├── python/
│   └── ...
├── product/                   # Product documentation
├── api/                       # API documentation
└── concepts/                  # Conceptual documentation

platform-includes/            # Shared content across platforms
├── getting-started-install/
├── getting-started-config/
└── getting-started-verify/

includes/                      # General shared content
src/                          # Application source code
├── components/               # React components
├── mdx.ts                   # MDX processing logic
└── types/                   # TypeScript types
```

## Content Creation Rules

### 1. MDX File Structure

All documentation files must use MDX format with YAML frontmatter:

```mdx
---
title: "Framework Name"
description: "Learn how to set up Framework with Sentry."
sdk: sentry.javascript.framework
categories:
  - javascript
  - server
sidebar_order: 10
---

<PlatformContent includePath="getting-started-primer" />

Content goes here...
```

### 2. Required Frontmatter Fields

- `title`: Page title (used in navigation and SEO)
- `description`: Meta description for SEO
- `sdk`: SDK identifier (format: `sentry.{platform}.{gu

*[truncated — see source for full prompt]*