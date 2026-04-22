# CLAUDE

> ## What This Is

Pixelpit is an autonomous game jam duo: **Pit** (coder) and **Dither** (designer). They collaborate to ship small, polished games.

#

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Pixelpit — Claude Code Instructions

## What This Is

Pixelpit is an autonomous game jam duo: **Pit** (coder) and **Dither** (designer). They collaborate to ship small, polished games.

## Agents

| Agent | Role | Status |
|-------|------|--------|
| **Pit** | Coder — implements games | OpenClaw agent |
| **Dither** | Designer — concepts, visuals, feel | Coming soon |

## Game Requirements (Non-Negotiable)

### Platform Support
- **MUST work on iPhone Safari** — touch input, iOS audio quirks
- **MUST work on desktop Chrome/Safari** — mouse + keyboard
- **Test on both before shipping**

### Technical Constraints
- **Single HTML file** — all JS/CSS inline
- **No external dependencies** — no CDN links, no npm
- **Canvas-based** — 2D context, `requestAnimationFrame` loop
- **Responsive** — adapt to screen size, handle orientation

### iOS Audio Quirk
Web Audio API requires a user gesture to start. Handle it:

```javascript
let audioCtx;
function initAudio() {
  if (!audioCtx) {
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  }
  if (audioCtx.state === 'suspended') {
    audioCtx.resume();
  }
}
// Call initAudio() on first touch/click
canvas.addEventListener('touchstart', initAudio, { once: true });
canvas.addEventListener('click', initAudio, { once: true });
```

### Input Handling
Support both touch and mouse:

```javascript
// Unified input
canvas.addEventListener('touchstart', (e) => {
  e.preventDefault();
  const touch = e.touches[0];
  handleInput(touch.clientX, touch.clientY);
});
canvas.addEventListener('mousedown', (e) => {
  handleInput(e.clientX, e.clientY);
});

// Keyboard for desktop
document.addEventListener('keydown', (e) => {
  if (e.code === 'Space') jump();
  if (e.code === 'ArrowLeft') moveLeft();
  if (e.code === 'ArrowRight') moveRight();
});
```

## Visual Style

Use the RAIN theme palette:

```javascript
const THEME = {
  bg: '#0f172a',       // Deep blue-black
  surface: '#1e293b',  // Slate
  gold: '#fbbf24',     /

*[truncated — see source for full prompt]*