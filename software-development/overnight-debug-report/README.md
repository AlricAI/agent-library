# Overnight Debug Report

> **Date:** 2026-01-30  
**System:** Raspberry Pi 5 Model B Rev 1.1, Debian Trixie (13), Kernel 6.12.47+rpt-rpi-2712

---

## Issue 1: rpicam + Hailo "H

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Overnight Debug Report — Raspberry Pi 5 Hardware Issues

**Date:** 2026-01-30  
**System:** Raspberry Pi 5 Model B Rev 1.1, Debian Trixie (13), Kernel 6.12.47+rpt-rpi-2712

---

## Issue 1: rpicam + Hailo "HailoRT not ready"

### Summary

The "HailoRT not ready!" message is **expected behavior** during `rpicam-still` capture — it is NOT a Hailo failure. The Hailo-8 NPU inference actually works correctly during the viewfinder/preview phase. A separate kernel driver bug (find_vma locking) was found and patched.

### Root Cause Analysis

**The "HailoRT not ready!" message is benign in the still capture context.**

The rpicam Hailo postprocessing pipeline requires three conditions to be met (`Ready()` method in `hailo_postprocessing_stage.hpp:160`):
```cpp
bool Ready() const { return init_ && low_res_stream_ && output_stream_; }
```

When `rpicam-still` operates, it goes through two phases:
1. **Viewfinder phase** (lores stream active) → Inference runs successfully
2. **Still capture phase** (lores stream torn down for full-res) → `low_res_stream_` becomes null → `Ready()` returns false → "HailoRT not ready!" printed

**Evidence that inference works correctly:**
- `rpicam-hello` with Hailo post-processing: ✅ No errors, runs for full duration
- `rpicam-vid` with Hailo post-processing: ✅ No errors, runs for full duration  
- `rpicam-still` viewfinder phase: ✅ No errors (streams include 640x640 BGR888 lores)
- `rpicam-still` capture phase: ❌ "HailoRT not ready!" (expected — no lores stream)

### Kernel Driver Bug Found & Fixed

The out-of-tree `hailo_pci` driver (v4.23.0, from `hailort-pcie-driver` package) had a **missing mmap_read_lock bug** in `hailo_vdma_buffer_map()`:

**File:** `/usr/src/hailort-pcie-driver/linux/vdma/memory.c` line 170  
**Bug:** `find_vma(current->mm, addr_or_fd)` called without holding `mmap_read_lock`  
**Kernel requirement:** Linux 6.12 requires `mmap_read_lock` before `find_vma()`  
**Symptom:** Kernel WARNING at `include/linux/rwsem.h:80` wi

*[truncated — see source for full prompt]*