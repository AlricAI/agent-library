# OPENVINO BUILD

> Compile and run **remembrances-mcp** with hardware-accelerated inference on Intel GPUs and NPUs using the [Intel OpenVINO](https://github.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Intel OpenVINO Build Guide

Compile and run **remembrances-mcp** with hardware-accelerated inference on Intel GPUs and NPUs using the [Intel OpenVINO](https://github.com/openvinotoolkit/openvino) backend for llama.cpp/ggml.

## Supported Hardware

| Device class | Examples | Support status |
|---|---|---|
| Intel iGPU (Xe-LPG / Arc) | Arrow Lake-U, Meteor Lake, Raptor Lake GT2 | ✅ Production |
| Intel Arc discrete GPU | Arc A770, Arc B580 | ✅ Production |
| Intel NPU (AI Boost) | Arrow Lake NPU (`/dev/accel/accel0`), Meteor Lake NPU | ✅ Supported (experimental) |
| Intel CPU (fallback) | Any x86-64 with AVX2 | ✅ Always available |

This repository was developed on a system with:
- **CPU/iGPU**: Intel Arrow Lake-U `00:02.0 Intel Corporation Arrow Lake-U [Intel Graphics]`
- **NPU**: Intel Arrow Lake NPU `00:0b.0 Processing accelerators: Intel Corporation Arrow Lake NPU`
- **Kernel**: Linux 6.18 with `i915`, `xe`, and `intel_vpu` modules loaded
- **NPU device**: `/dev/accel/accel0`

---

## Architecture Overview

The OpenVINO backend in llama.cpp/ggml:
- CMake flag: `-DGGML_OPENVINO=ON`
- Produces: `libggml-openvino.so` alongside `libggml.so` / `libllama.so`
- Requires: OpenVINO SDK (C++ headers + CMake config + runtime libraries)
- Runtime device selection: `CPU`, `GPU`, `NPU` (set via env or build flag)
- Falls back to CPU when GPU/NPU is unavailable

---

## Prerequisites

### 1. OpenVINO SDK

**Option A – APT from Intel (recommended for production)**

```bash
# Add Intel APT repository
curl -fsSL https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS.PUB \
  | sudo gpg --dearmor -o /usr/share/keyrings/intel-sw-products.gpg

echo "deb [signed-by=/usr/share/keyrings/intel-sw-products.gpg] \
  https://apt.repos.intel.com/openvino/2025 ubuntu24 main" \
  | sudo tee /etc/apt/sources.list.d/intel-openvino.list

sudo apt-get update
sudo apt-get install -y openvino openvino-dev
# SDK is installed at /opt/intel/openvino/
# CMake config: /opt/intel/openvi

*[truncated — see source for full prompt]*