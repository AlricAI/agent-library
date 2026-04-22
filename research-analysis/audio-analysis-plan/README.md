# AUDIO ANALYSIS PLAN

> ## Vision

Give Jambot **ears that can describe what they hear** in producer terms:
- "Kick fundamental: E1 (41Hz), -2 cents flat"
- "Bass: squelchy (

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Jambot Audio Analysis: Real Upgrade Plan

## Vision

Give Jambot **ears that can describe what they hear** in producer terms:
- "Kick fundamental: E1 (41Hz), -2 cents flat"
- "Bass: squelchy (resonance peak at 1.2kHz, 12dB above neighbors)"
- "Mud warning: 340Hz buildup, kick+bass masking"
- "Sidechain: attack 8ms, release 180ms — release is eating the next hat"

---

## Current State

The existing `analyze-node.js` provides:
- Basic stats: duration, sample rate, peak/RMS levels
- Frequency balance: 4 broad bands (20-250Hz, 250-1k, 1k-4k, 4k-20k)
- Sidechain detection: amplitude dips, pattern guess, avg ducking depth
- Waveform detection: saw/square/triangle/sine classification
- Spectrogram generation (via sox)

### Gaps

| Question | Current Answer |
|----------|----------------|
| "Is this squelchy?" | NO - can't detect resonance peaks |
| "Kick is in E?" | BARELY - no Hz→note, no percussive pitch detection |
| "Where's the mud?" | PARTIALLY - 250-1kHz too broad |
| "Sidechain timing ok?" | BARELY - no attack/release measurement |

---

## Architecture

```
jambot/effects/
  analyze-node.js          # Current (keep for basic stats)
  spectral-analyzer.js     # NEW: FFT-based analysis
  pitch-detector.js        # NEW: Pitch detection for kicks/bass
  timing-analyzer.js       # NEW: Sidechain/envelope analysis

jambot/tools/
  analyze-tools.js         # Update with new tools
```

### New Tools for Agent

| Tool | What it answers |
|------|-----------------|
| `detect_pitch` | "What note is this kick/bass?" |
| `detect_resonance` | "Is this squelchy? Where's the peak?" |
| `detect_mud` | "Where's the frequency buildup?" |
| `analyze_sidechain_timing` | "Is the attack/release right?" |
| `describe_sound` | "Describe this in producer terms" |

---

## Phase 1: Spectral Analyzer (2-3 days)

### File: `jambot/effects/spectral-analyzer.js`

```javascript
/**
 * SpectralAnalyzer - FFT-based audio analysis
 *
 * Uses sox's stat -freq or a pure JS FFT for spectral analysi

*[truncated — see source for full prompt]*