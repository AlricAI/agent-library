# Tts

> ## 🎯 Purpose

Provide an in-browser TTS player that reads page content aloud using the Web Speech API, with sentence highlighting, auto-scroll, and a

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🎧 Text-to-Speech Player

## 🎯 Purpose

Provide an in-browser TTS player that reads page content aloud using the Web Speech API, with sentence highlighting, auto-scroll, and auto-play navigation.

## 🏗️ Architecture

### 📦 Components

- **TextToSpeech.tsx** — React component rendering the player UI (controls, progress bar, toggle)
- **tts.inline.ts** — Client-side engine: content extraction, speech synthesis, playback state
- **tts.utils.ts** — Pure utility functions (emoji stripping, sentence splitting, time estimation)
- **tts.autoplay.ts** — Auto-navigation between pages via series links or BFS
- **tts.scss** — Fixed bottom-right player styling

### 📖 Content Extraction

The `extractArticleBlocks()` function builds a list of text blocks from:

1. **Article content** — Block-level elements (`p`, `li`, `h1`–`h6`, `td`, `th`, `dd`, `dt`, `figcaption`, `summary`) inside `<article>`, excluding noise containers (nav, header, footer, sidebar, backlinks, code blocks, math, diagrams)
2. **Static giscus comments** — The `[data-static-giscus]` section, if present. Each comment is read as "Comment by [author]" followed by the comment body paragraphs

**Excluded sections:**
- Social media embed sections (headings containing Tweet, Bluesky, or Mastodon) and all content beneath them are skipped entirely. The `SOCIAL_SECTION_HEADINGS` constant in `tts.utils.ts` defines the platform names to detect.

Inline noise (code, SVG, KaTeX, buttons) is stripped from cloned elements before text extraction. Emoji and residual Markdown characters are removed. Blocks lacking terminal punctuation receive a semicolon for natural TTS pauses.

### 🗣️ Playback

- Sentences are spoken via `SpeechSynthesisUtterance` at configurable rate (0.5×–2×)
- Each sentence maps back to its source DOM block for highlighting and auto-scroll
- Time estimates use 150 WPM baseline
- Screen Wake Lock prevents sleep during playback
- Speed preference persists across SPA navigations

### ⏭️ Auto-Play

When enab

*[truncated — see source for full prompt]*