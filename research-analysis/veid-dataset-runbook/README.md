# Veid Dataset Runbook

> This document describes the procedures for building, validating, and approving VEID training datasets.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VEID Dataset Build and Approval Runbook

This document describes the procedures for building, validating, and approving VEID training datasets.

## Overview

The VEID dataset pipeline provides a production-grade system for:

- Ingesting identity verification data from multiple sources
- Anonymizing PII before processing
- Applying labels (human review + heuristics)
- Creating deterministic train/val/test splits
- Generating signed manifests for audit trails
- Tracking complete dataset lineage

## Quick Start

### Generate Synthetic Dataset (CI/Development)

```bash
# Minimal synthetic dataset for CI tests
python -m ml.training.build_dataset synthetic \
    --output data/synthetic/ci \
    --profile ci_minimal

# Standard development dataset
python -m ml.training.build_dataset synthetic \
    --output data/synthetic/dev \
    --profile dev_medium \
    --seed 42
```

### Build Production Dataset

```bash
python -m ml.training.build_dataset build \
    --source /data/veid/raw \
    --output /data/veid/v1.0.0 \
    --version 1.0.0 \
    --sign \
    --signer-id production-builder
```

### Validate Existing Dataset

```bash
python -m ml.training.build_dataset validate \
    --dataset /data/veid/v1.0.0 \
    --report validation_report.json \
    --fail-on-error
```

## Dataset Build Workflow

### 1. Data Collection

Data can be ingested from multiple sources:

| Source Type | URI Format | Example |
|-------------|------------|---------|
| Local Files | `/path/to/data` | `/data/veid/batch_001` |
| AWS S3 | `s3://bucket/prefix` | `s3://veid-data/raw/2024` |
| Google Cloud Storage | `gs://bucket/prefix` | `gs://veid-data/raw/2024` |
| HTTP API | `https://api.example.com` | `https://api.veid.io/v1/data` |

Each source must contain samples in the expected format:

```
data/
├── manifest.json      # Optional manifest file
├── sample_001/
│   ├── metadata.json  # Sample metadata
│   ├── document.png   # Document image
│   └── selfie.png     # Selfie image
├── sample_002/
│   

*[truncated — see source for full prompt]*