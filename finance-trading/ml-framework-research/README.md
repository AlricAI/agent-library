# Ml Framework Research

> > **Issue**: tb-v8l | **Date**: 2026-02-20
> **Purpose**: Evaluate ML frameworks for Node.js trading signal prediction

## Executive Summary

For real

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ML Framework Research: TensorFlow.js vs brain.js vs ONNX Runtime

> **Issue**: tb-v8l | **Date**: 2026-02-20
> **Purpose**: Evaluate ML frameworks for Node.js trading signal prediction

## Executive Summary

For real-time signal scoring on 15+ features in our Node.js trading bot, **ONNX Runtime** is the recommended framework. It provides the best inference performance, supports all model types we need (including gradient boosted trees which are the strongest fit for tabular trading data), and enables a "train in Python, deploy in Node.js" workflow that gives us access to the full Python ML ecosystem without runtime overhead.

---

## Comparison Matrix

| Dimension | TensorFlow.js | brain.js | ONNX Runtime |
|---|---|---|---|
| **npm package** | `@tensorflow/tfjs-node` | `brain.js` | `onnxruntime-node` |
| **Version** | 4.22.0 (Oct 2024) | 2.0.0-beta.24 | 1.24.1 (Jan 2026) |
| **npm weekly downloads** | ~114k | ~3.8k | ~651k |
| **GitHub stars** | ~18.5k | ~14.9k | ~19.2k |
| **Maintainer** | Google | Community (1-2 devs) | Microsoft |
| **License** | Apache-2.0 | MIT | MIT |
| **Install size** | ~350-500 MB | ~4.3 MB (+ gpu.js peer) | ~30-50 MB (CPU-only) |
| **Native deps** | libtensorflow C binary | headless-gl (optional) | Pre-built .node addon |
| **Training in Node.js** | Yes (full Keras-like API) | Yes (simple API) | No (inference-only) |
| **Inference latency** | ~0.1-1 ms (tfjs-node) | sub-ms (small nets) | ~0.5-2.5 ms |
| **Node 20/22 compat** | Problematic (binary issues) | Unknown (beta) | Supported |
| **Maintenance status** | Slowing (no release since Oct 2024) | Low (perpetual beta) | Very active |

### Model Type Support

| Model Type | TensorFlow.js | brain.js | ONNX Runtime |
|---|---|---|---|
| Dense / MLP | Train + Infer | Train + Infer | Infer (train in Python) |
| LSTM | Train + Infer | Train + Infer | Infer (train in Python) |
| GRU | Train + Infer | Train + Infer | Infer (train in Python) |
| CNN | Train + Infer | Not supported | Infer (trai

*[truncated — see source for full prompt]*