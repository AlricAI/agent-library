# PODCAST PROCESSING MASTER PLAN

> ## CURRENT IMPLEMENTATION STATUS

This document outlines the original master plan for podcast processing. Significant progress has been made, and some

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PODCAST PROCESSING MASTER PLAN - COMPLETE IMPLEMENTATION GUIDE

## CURRENT IMPLEMENTATION STATUS

This document outlines the original master plan for podcast processing. Significant progress has been made, and some aspects have been implemented differently or superseded by the `SmartTranscriptionPipeline`.

**Key Updates:**
- **RSS Feed Ingestion:** Implemented directly within `helpers/smart_transcription_pipeline.py` using `feedparser`, driven by `config/podcasts_prioritized_cleaned.csv`.
- **Podcast Configuration:** Centralized in `config/podcasts_prioritized_cleaned.csv`, including RSS URLs and processing preferences.
- **Episode Queuing:** Episodes are queued for processing in `processing_queue.db` by `SmartTranscriptionPipeline`.
- **Transcription:** Handled by `SmartTranscriptionPipeline` via Mac Mini integration (SSH + Whisper), or by direct transcript fetching for `transcript_only` podcasts.
- **Database:** Transcripts are saved to `atlas.db`'s `content` table.

**Remaining Critical Step:** Full setup and configuration of the Mac Mini for transcription processing.

## CRITICAL PROBLEM ANALYSIS

**ORIGINAL BROKEN STATE (largely addressed):**
- Database had 6 "podcast" entries that were actually ARTICLES about podcasts (now clarified with dedicated podcast processing).
- No RSS feed ingestion system existed (now integrated into `SmartTranscriptionPipeline`).
- Scheduler ran 3 minutes then exited (addressed by `SmartTranscriptionPipeline`'s continuous processing and queuing).
- All podcast processing code processed nothing because no episodes existed (now episodes are discovered and queued).
- User expects thousands of real podcast episodes with transcripts (now achievable through the implemented pipeline).

**CURRENT FOCUS:** Ensuring the Mac Mini transcription setup is fully operational for end-to-end processing.

**ROOT CAUSE (original):** Built processing systems without data ingestion foundation (now resolved for podcasts).

## COMPLETE ARCHITECTURE DESI

*[truncated — see source for full prompt]*