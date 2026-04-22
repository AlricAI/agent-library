# Render Frame Gate Plan

> ## Context

WebP animations stutter during Giphy channel refreshes, while GIF animations play smoothly. The root cause is **L2 cache contention** betw

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Plan: Render Frame Gate for Stutter-Free Animation Playback

## Context

WebP animations stutter during Giphy channel refreshes, while GIF animations play smoothly. The root cause is **L2 cache contention** between the render pipeline (Core 1, priority 8) and the Giphy refresh task (Core 0, priority 4).

The ESP32-P4's 256KB L2 cache is shared between both cores. During a Giphy refresh, heavy PSRAM operations pollute the cache:
- HTTP response receive: ~94KB written to PSRAM buffer per page (6 pages typical)
- cJSON parsing: hundreds of heap-allocated nodes from ~94KB JSON
- Hash table merging/eviction: random PSRAM pointer chasing

These evict cache lines that the WebP decoder needs, pushing decode time past the VSYNC deadline (~16.6ms at 60Hz). Frames that miss their VSYNC window display for 33ms instead of 16.6ms = visible stutter.

**Why WebP and not GIF**: WebP decode (`WebPAnimDecoderGetNext`) has a large working set (~700KB+: compressed data + VP8L decode state + full RGBA output) that already exceeds the L2 cache. Any additional cache pressure from concurrent PSRAM access causes cache thrashing. GIF decode uses incremental palette-based updates with a small working set (~1KB palette + only changed rectangles), which is cache-resilient.

## Approach: Render Frame Gate

A cooperative yielding mechanism where the render task signals when it's actively decoding a frame, and network/refresh tasks check this signal and yield during their cache-heavy operations.

This follows the existing `animation_player_is_sd_paused()` pattern already used by `download_manager.c` and `makapix_channel_impl.c` (weak extern symbols from `main/`).

## Changes

### 1. Display renderer: add gate flag and wrap frame callback

**`main/display_renderer.c`** (~line 30, add flag):
```c
static volatile bool g_frame_rendering_active = false;
```

Add three functions:
```c
void display_renderer_frame_gate_enter(void) { g_frame_rendering_active = true; }
void display_renderer_frame_gate_leav

*[truncated — see source for full prompt]*