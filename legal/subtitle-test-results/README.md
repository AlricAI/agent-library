# Subtitle Test Results

> **Date:** 2026-01-30  
**Platform:** Raspberry Pi 5 (aarch64), Debian, ffmpeg 7.1.3, faster-whisper (base, int8, CPU)

## Files Created

- `/home/claw

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Subtitle Tool Test Results

**Date:** 2026-01-30  
**Platform:** Raspberry Pi 5 (aarch64), Debian, ffmpeg 7.1.3, faster-whisper (base, int8, CPU)

## Files Created

- `/home/clawd/scripts/subtitle.py` — Main Python script
- `/home/clawd/scripts/subtitle.sh` — Shell wrapper (activates whisper venv)

## Test Summary

### Test 1: Camera clip (no audio track)
- **Input:** 5s Pi camera MJPEG → H.264 MP4 (1920×1080, no audio)
- **Command:** `subtitle.sh /tmp/test_subtitle.mp4`
- **Result:** ✅ Gracefully handled missing audio track, wrote empty `.srt`
- **Output:** `/tmp/test_subtitle.srt` (0 bytes)

### Test 2: Silent audio track
- **Input:** Same video + silent AAC audio track added via ffmpeg
- **Command:** `subtitle.sh /tmp/test_subtitle_audio.mp4`
- **Result:** ✅ Model loaded, detected English (prob 0.55), 0 segments (correct — no speech)
- **Output:** `/tmp/test_subtitle_audio.srt` (0 bytes)

### Test 3: Burn subtitles (hardcoded)
- **Input:** Video + manually created SRT with 2 cues
- **Method:** Direct call to `burn_subtitles()` function
- **Result:** ✅ ffmpeg burned subs with libass, white text + black outline, bottom-aligned
- **Output:** `/tmp/test_burned_direct.mp4` (2.7 MB)
- **Style:** Arial 22pt, white primary, black outline (2px), shadow, bottom-center, 40px margin

### Test 4: Embed soft subtitles
- **Input:** Video + SRT file
- **Method:** Direct call to `embed_subtitles()` function
- **Result:** ✅ ffprobe confirms 3 streams: video (h264), audio (aac), subtitle (mov_text/tx3g, eng)
- **Output:** `/tmp/test_embedded_direct.mp4` (4.3 MB)

### Test 5: Graceful skip on empty segments
- **Command:** `subtitle.sh /tmp/test_subtitle_audio.mp4 --burn --embed`
- **Result:** ✅ Correctly skipped burn/embed when 0 segments detected, no crash

### Test 6: --translate flag (placeholder)
- **Command:** `subtitle.sh /tmp/test_subtitle.mp4 --translate`
- **Result:** ✅ Prints placeholder message, continues normally

## Usage

```bash
# Generate SRT only
./subtitle.sh inp

*[truncated — see source for full prompt]*