# Text To Speech

> A browser-native Text-to-Speech player embedded on every page, powered by the
[Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Speech

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Text-to-Speech (TTS) Audio Player

A browser-native Text-to-Speech player embedded on every page, powered by the
[Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis)
(`SpeechSynthesis`). Zero external dependencies, free, no ads.

## Features

### Player Controls
| Control | Description |
|---------|-------------|
| **Play / Pause** | Start or pause reading. Uses `synth.cancel()` for reliable cross-utterance pausing. |
| **Skip ±30 s** | Jump forward or backward approximately 30 seconds (estimated via word counts). |
| **Speed selector** | Choose 0.5×, 0.75×, 1×, 1.25×, 1.5×, 1.75×, or 2× playback rate. |
| **Seek bar** | Drag to jump to any point in the article. Shows elapsed and total estimated time. |

### Always-Fixed Collapsible Player
The player is permanently fixed at the bottom-right corner of the viewport.
A small **🔊 toggle tab** sits above the player panel. Tapping the tab slides
the player panel down out of view; tapping again brings it back. When collapsed,
only the tab remains visible at the bottom-right corner. If a `FixedFooter`
element is present on the page, the player positions itself above it automatically.

### Text Extraction
The player reads only the `<article>` content. The following are stripped:

- **Navigation & chrome** — `nav`, `header`, `footer`, `.sidebar`, `.backlinks`,
  `.graph`, `.toc`, `.explorer`, `.search`, `button`
- **Code & technical blocks** — `pre`, `script`, `style`, `code` (inline)
- **Visual-only content** — `svg`, `.katex`, `.mermaid`, `.external-icon`
- **The TTS player itself** — `.tts-container`

Within each block element, the player clones the node (to avoid mutating the
live DOM), removes inline junk selectors, then runs the text through `cleanText()`.

### Emoji Stripping
All emoji are removed before the synthesiser reads the text. This avoids the
browser vocalising emoji names (e.g. "house with garden" for 🏡). The
`stripEmojis()` function targets:

| Category | Unicode Range | Exa

*[truncated — see source for full prompt]*