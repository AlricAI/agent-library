# Og Image Compositing

> ## 📋 Overview

🎯 The OG image compositing system enhances auto-generated Open Graph social preview images by incorporating content-specific images f

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🖼️ OG Image Compositing — Product & Engineering Design Spec

## 📋 Overview

🎯 The OG image compositing system enhances auto-generated Open Graph social preview images by incorporating content-specific images from notes alongside branded metadata.

🏗️ When a note contains an embedded image or references a YouTube video, the OG preview combines:
1. **Branded text metadata** — title, description, date, reading time, tags, site icon
2. **Content image** — the first embedded image from the note or a YouTube video thumbnail

📐 Notes without embedded images continue to use the existing text-only OG template.

---

## 🧩 Architecture

```
                    processOgImage()
                         │
            ┌────────────┼────────────┐
            ▼            ▼            ▼
    extractFirstLocal  extractYouTube  (no image)
    ImageRef()         VideoId()
            │            │            │
            ▼            ▼            │
    loadContentImage   fetchYouTube   │
    Base64()           ThumbnailBase64()
            │            │            │
            └────────────┼────────────┘
                         ▼
               generateSocialImage()
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
    defaultImage (with image) defaultImage (text-only)
    ┌──────────────┬──────┐  ┌──────────────────┐
    │ Title/Meta   │ IMG  │  │ Title/Meta       │
    │ Description  │      │  │ Description      │
    │ Tags         │      │  │ Tags             │
    └──────────────┴──────┘  └──────────────────┘
```

---

## 🔄 Content Image Resolution

### 📎 Local Image Extraction

🔍 The system scans the VFile raw markdown (`vfile.value`) for the first local image reference. Note: `fileData.text` is plain text extracted from the HTML AST by the Description transformer, which strips all image syntax. The raw markdown from `vfile.value` preserves the original image references needed for extraction.

1. **Markdown imag

*[truncated — see source for full prompt]*