# Feature Extraction

> ## Overview

The feature extraction pipeline transforms decrypted identity scopes into ML feature vectors for the VEID identity scoring system. This d

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Feature Extraction Pipeline

## Overview

The feature extraction pipeline transforms decrypted identity scopes into ML feature vectors for the VEID identity scoring system. This document describes the architecture, components, and usage of the feature extraction subsystem.

## Architecture

```
┌─────────────────────┐
│  Decrypted Scopes   │
│  (Selfie, ID Doc,   │
│   Video, etc.)      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│    Media Parser     │
│  - Format detection │
│  - Image/Video/JSON │
│  - Validation       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  Feature Extractor  │
│  - Face embedding   │
│  - Liveness signals │
│  - OCR features     │
│  - Quality metrics  │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│   Quality Gates     │
│  - Blur detection   │
│  - Brightness check │
│  - OCR confidence   │
│  - Face confidence  │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│   ML Feature Vector │
│   (768 dimensions)  │
└─────────────────────┘
```

## Components

### Media Parser (`x/veid/keeper/media_parser.go`)

Parses decrypted scope payloads into typed media content.

**Supported Formats:**
- **Images**: JPEG, PNG, WebP
- **Videos**: MP4, WebM, AVI
- **JSON**: SSO metadata, email/SMS proofs

**Usage:**
```go
parser := NewMediaParser()
payload, err := parser.Parse(decryptedScope)
if err != nil {
    return err
}

switch payload.MediaType {
case MediaTypeImage:
    // Process image
    width := payload.ImageData.Width
    height := payload.ImageData.Height
case MediaTypeVideo:
    // Process video
    frames := payload.VideoData.EstimatedFrameCount
case MediaTypeJSON:
    // Process structured data
    data := payload.JSONData
}
```

### Feature Extraction Pipeline (`x/veid/keeper/feature_extraction.go`)

Orchestrates extraction of all ML features from parsed media.

**Extracted Features:**

| Feature Group | Dimensions | Desc

*[truncated — see source for full prompt]*