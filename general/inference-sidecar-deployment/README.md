# Inference Sidecar Deployment

> ## Overview

The VEID inference sidecar provides deterministic ML inference for identity scoring
in a blockchain consensus environment. This document 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Inference Sidecar Deployment Guide

## Overview

The VEID inference sidecar provides deterministic ML inference for identity scoring
in a blockchain consensus environment. This document describes the deployment topology
and resource requirements.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Validator Node                          │
│  ┌─────────────────┐     gRPC      ┌──────────────────────┐ │
│  │   VirtEngine    │◄─────────────►│  Inference Sidecar   │ │
│  │   (Chain Node)  │  localhost:   │  (TensorFlow Model)  │ │
│  │                 │    50051      │                      │ │
│  └─────────────────┘               └──────────────────────┘ │
│         │                                   │               │
│         ▼                                   ▼               │
│  ┌─────────────────┐               ┌──────────────────────┐ │
│  │   Prometheus    │◄──────────────│  /metrics (9090)     │ │
│  │   Metrics       │               │                      │ │
│  └─────────────────┘               └──────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

## Deployment Modes

### 1. Sidecar Mode (Recommended for Production)

The inference sidecar runs as a separate process alongside the validator node.
This provides:
- Memory isolation between chain and inference
- Independent scaling and resource management
- Easier model updates without chain restarts

**Configuration:**
```bash
# On the validator node
export VEID_INFERENCE_ENABLED=true
export VEID_INFERENCE_USE_SIDECAR=true
export VEID_INFERENCE_SIDECAR_ADDR=localhost:50051
export VEID_INFERENCE_MODEL_HASH=<expected-model-hash>
```

**Starting the sidecar:**
```bash
./inference-sidecar \
    --grpc-addr=:50051 \
    --metrics-addr=:9090 \
    --model-path=/models/trust_score \
    --model-version=v1.0.0 \
    --expected-hash=<model-hash> \
    --force-cpu=true \
    --random-seed=42
```

### 2. Embedded Mode (Devel

*[truncated — see source for full prompt]*