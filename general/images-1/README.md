# IMAGES

> This document covers how to use images in the Monsoft Solutions website, with a focus on blog posts.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Images Documentation

This document covers how to use images in the Monsoft Solutions website, with a focus on blog posts.

## Overview

Astro provides built-in image optimization through the `<Image />` component. Images are automatically:

- Optimized and compressed
- Converted to modern formats (WebP/AVIF)
- Lazy-loaded for performance
- Sized to prevent layout shift

## Image Locations

### Local Images (Recommended)

Store images in `src/` for automatic optimization:

```
src/
├── assets/
│   └── blog/           # Shared blog images
│       └── hero-default.jpg
├── data/
│   └── blog/
│       ├── my-post.md
│       └── images/     # Post-specific images
│           ├── hero.jpg
│           └── diagram.png
```

### Public Images (No Optimization)

Images in `public/` are served as-is without processing:

```
public/
└── images/
    └── og-default.jpg  # For external URLs, social sharing
```

## Blog Post Images

### Hero Image (Featured Image)

The hero image appears at the top of the blog post and is used for:

- Visual header on the post page
- Social sharing previews (Open Graph)
- Blog listing cards (if implemented)

**Frontmatter:**

```yaml
---
title: 'My Post Title'
heroImage: './images/hero.jpg' # Relative to the .md file
heroImageAlt: 'Description of image for accessibility'
---
```

**Specifications:**
| Property | Recommendation |
|----------|---------------|
| Dimensions | 1200×630px (16:9 for social) |
| Format | JPG or PNG (WebP auto-generated) |
| File size | Under 500KB before optimization |
| Aspect ratio | 16:9 preferred |

### Inline Images

Add images within your markdown content:

```markdown
## My Section

Here's an explanation with a visual:

![Diagram showing the automation flow](./images/automation-flow.png)

More text continues here...
```

**Best Practices:**

- Use descriptive alt text for accessibility
- Place images after introducing the concept
- Keep file sizes reasonable (under 300KB each)
- Use PNG for diagrams/screenshots, JP

*[truncated — see source for full prompt]*