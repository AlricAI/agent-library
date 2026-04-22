# BLOG WRITING SKILL

> This document defines the guidelines for creating SEO-optimized, engaging blog posts for Monsoft Solutions.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Blog Writing Skill

This document defines the guidelines for creating SEO-optimized, engaging blog posts for Monsoft Solutions.

**Related Documents:**

- [BLOG-TOPICS.md](./BLOG-TOPICS.md) — Topic clusters, content gaps, and audience segmentation
- [TARGET_AUDIENCE.md](./TARGET_AUDIENCE.md) — Detailed audience profiles and messaging guidelines

---

## Blog Post Structure

Every blog post should follow this structure:

```
src/data/blog/
├── post-slug/
│   ├── index.md          # The blog post content
│   └── images/           # Post-specific images
│       ├── hero.jpg      # Featured image (1200x630)
│       ├── inline-1.jpg  # First inline image
│       ├── inline-2.jpg  # Second inline image
│       └── inline-3.jpg  # Third inline image (optional)
```

## Frontmatter Template

```yaml
---
title: 'Your Compelling Title Here' # Max 70 chars
description: 'A compelling meta description' # Max 160 chars
pubDate: 2026-01-31
author: 'Monsoft Solutions'
category: 'AI & Automation' # See allowed categories
tags: ['AI', 'Automation', 'Business'] # 3-5 relevant tags
featured: false # true for hero placement
draft: false # true to hide from prod
readingTime: '7 min read'
heroImage: './images/hero.jpg'
heroImageAlt: 'Descriptive alt text for the hero image'
---
```

### Allowed Categories

- AI & Automation
- Web Development
- Business Growth
- Technology Trends
- Case Studies
- Guides & Tutorials
- Local Business
- Medical & Aesthetics

---

## E-E-A-T Guidelines for YMYL Content

Medical and aesthetics content is classified as YMYL (Your Money or Your Life) by Google. These topics require higher E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness) standards.

### Experience

- Include real implementation stories and case studies
- Reference specific client outcomes (with permission)
- Share practical lessons learned from actual deployments
- Use first-hand examples: "In our work with aesthetic practices, we've found..."

### Expertise

- Use correct medi

*[truncated — see source for full prompt]*