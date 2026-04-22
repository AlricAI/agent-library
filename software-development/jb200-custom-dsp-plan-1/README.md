# JB200 CUSTOM DSP PLAN

> ## The Problem

JB200 sounds different between web UI and Jambot, even though they share the same engine code.

**Root cause**: The engine uses Web Au

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# JB200 Custom DSP Plan

## The Problem

JB200 sounds different between web UI and Jambot, even though they share the same engine code.

**Root cause**: The engine uses Web Audio API's built-in oscillator (`osc.type = 'sawtooth'`), which is a black box. Different platforms implement it differently:
- **Browser**: Native Web Audio (Chrome/Safari/Firefox)
- **Jambot**: `node-web-audio-api` (Node.js package)

Same code, different oscillator implementations = different sound.

## The Solution

Replace platform-dependent oscillators with custom `PeriodicWave` definitions. We provide the exact harmonic coefficients, both platforms generate identical waveforms.

## Phase 1: Custom Oscillators (LOW RISK)

### What Changes

In `web/public/jb200/dist/machines/jb200/engine.js`:

**Before:**
```javascript
const osc = context.createOscillator();
osc.type = 'sawtooth';
```

**After:**
```javascript
const osc = context.createOscillator();
osc.setPeriodicWave(this.waveforms.sawtooth);
```

### Waveform Definitions

```javascript
// Generate once at engine init, reuse for all notes
function createWaveforms(context, numHarmonics = 64) {
  return {
    sawtooth: createSawtooth(context, numHarmonics),
    square: createSquare(context, numHarmonics),
    triangle: createTriangle(context, numHarmonics),
  };
}

function createSawtooth(context, n) {
  const real = new Float32Array(n);
  const imag = new Float32Array(n);
  for (let i = 1; i < n; i++) {
    imag[i] = 1 / i;  // sawtooth = sum of sin(n)/n
  }
  return context.createPeriodicWave(real, imag);
}

function createSquare(context, n) {
  const real = new Float32Array(n);
  const imag = new Float32Array(n);
  for (let i = 1; i < n; i += 2) {
    imag[i] = 1 / i;  // square = odd harmonics only
  }
  return context.createPeriodicWave(real, imag);
}

function createTriangle(context, n) {
  const real = new Float32Array(n);
  const imag = new Float32Array(n);
  for (let i = 1; i < n; i += 2) {
    const sign = ((i - 1) / 2) % 2 === 0 ?

*[truncated — see source for full prompt]*