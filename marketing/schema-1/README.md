# Schema

> This document describes the YAML schema conventions for content files in the `/content` directory.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Content Schema Documentation

This document describes the YAML schema conventions for content files in the `/content` directory.

## Directory Structure

```
content/
├── index.yaml                    # Homepage content
├── business.json                 # Business information
├── socials.json                  # Social media links
├── privacy.md                    # Privacy policy
├── redirects.json                # URL redirects
└── services/
    └── [service-name]/
        ├── index.yaml            # Service page content
        ├── cover.jpg             # Service cover image (required)
        └── photos/               # Optional: Additional photos
            └── *.jpg, *.webp
```

## Service Page Schema (`/content/services/[name]/index.yaml`)

### Required Fields

- `title` (string): Service name displayed on the page
- `desc` (string): Short description (use `|-` for multi-line)
- `seo` (string): SEO meta description (use `|-` for multi-line)
- `image` (object): Cover image
  - `src` (string): Path to image relative to service directory (e.g., `./cover.jpg`)
  - `alt` (string): Alt text for accessibility (use `|-` for multi-line)

### Optional Fields

- `startPos` (string): Layout position - `"left"` or `"right"` (default: `"left"`)
- `draft` (boolean): Set to `true` to hide from production
- `sections` (array): Array of section objects (see Section Types below)

### Example

```yaml
title: Bathrooms
startPos: left
desc: |-
  Create your personal sanctuary, beautifully designed and customized to your exact preferences.
seo: |-
  Stylish bathroom remodels with bespoke vanities, premium stone tiles, and sleek fixtures.
image:
  src: ./cover.jpg
  alt: |-
    A modern bathroom featuring a sleek glass shower with marble tile.
sections:
  - type: Prices
    title: What's the cost?
    # ... section content
```

## Index Page Schema (`/content/index.yaml`)

### Required Fields

- `title` (string): Site title
- `desc` (string): Site description
- `popular` (array): 

*[truncated — see source for full prompt]*