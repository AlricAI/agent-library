# MUSIC KNOWLEDGE PROPOSAL

> ## Goal

Build a persistent music encyclopedia so Amber can:
1. Understand artists and genres you like in detail
2. Make tracks "in the style of X" wi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Amber Music Knowledge Base — Proposal

## Goal

Build a persistent music encyclopedia so Amber can:
1. Understand artists and genres you like in detail
2. Make tracks "in the style of X" with actual knowledge
3. Create mashups by combining known profiles
4. Develop taste over time through accumulated knowledge

## Two Approaches Compared

### Approach 1: Audio Fingerprinting (Premium)

**How it works:**
- Use [Cyanite API](https://cyanite.ai) or [Mureka](https://mureka.ai) to analyze actual audio
- Feed YouTube links, get back: tempo, energy, mood, instrumentation, similar tracks
- Store rich audio fingerprints

**Pros:**
- Objective, measurable data
- Catches sonic nuances text can't describe
- Can analyze any track, not just described ones

**Cons:**
- Cyanite: €290/month
- Adds API dependency
- Still need text for context (scene, influences, era)

### Approach 2: Text Research + Spotify (Recommended)

**How it works:**
- Web search for artist reviews, interviews, scene coverage
- Use free Spotify API for audio features (tempo, energy, danceability, valence)
- Build rich genre taxonomy manually
- You correct/enhance profiles over time

**Pros:**
- Free (Spotify API has generous free tier)
- Captures context audio can't (scene, era, influences, labels)
- Your corrections make it better than pure automation
- Works immediately with existing tools

**Cons:**
- Requires Spotify presence for audio features
- More manual effort
- May miss sonic details

**Recommendation:** Start with Approach 2. Add audio analysis later if needed.

---

## Data Model

### Artist Profile

```json
{
  "type": "music_artist",
  "content": "Johannes Brecht",
  "metadata": {
    "id": "johannes-brecht",

    "audio_profile": {
      "tempo_range": [120, 128],
      "energy": 0.7,
      "danceability": 0.8,
      "valence": 0.4,
      "acousticness": 0.1
    },

    "genres": ["techno", "house"],
    "subgenres": ["melodic techno", "deep house"],

    "signature_sounds": [
      "rolling ba

*[truncated — see source for full prompt]*