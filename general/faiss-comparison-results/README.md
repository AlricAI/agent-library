# Faiss Comparison Results

> ## Backend: Mojo SIMD (v3.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Faiss Comparison Results — March 12, 2026

## Backend: Mojo SIMD (v3.5.0)

This benchmark ran with Vectro in **Mojo SIMD mode** (`vectro_quantizer` binary built via
`pixi run build-mojo`). Python/NumPy fallback numbers are included for reference.

To reproduce:
```bash
pixi install && pixi shell
pixi run build-mojo
python benchmarks/benchmark_faiss_comparison.py --output results/faiss_comparison_mojo.json
```

---

## Summary

Vectro has been benchmarked against Faiss 1.13.2 on two key quantization metrics.

### INT8 Quantization Throughput

**Configuration:**
- 100,000 vectors of 768 dimensions
- Best-of-5 timed iterations (2 warmup iterations discarded)
- Hardware: Apple M3 Pro (quiet CPU — background processes terminated)

| Library | Throughput | vs FAISS |
|---------|:----------:|:--------:|
| Python/NumPy (baseline) | 61,589 vec/s | 0.02× |
| **Vectro Mojo SIMD** | **12,121,212 vec/s** | **4.59×** |
| FAISS C++ ScalarQuantizer | 2,639,653 vec/s | 1.00× |

**Key result:** Vectro Mojo SIMD is **4.59× faster than FAISS C++** at INT8 quantization.

The speedup comes from three compounding improvements over the Python fallback:
1. `SIMD_W=16`: tiles 4 NEON loads per `vectorize` call for software pipelining
2. `resize()` init: replaces per-element append loops with `memset`-equivalent init (~6× allocation speedup)
3. Pipe IPC: Python calls the Mojo binary via stdin/stdout, eliminating all disk I/O

### Product Quantization Quality (M=96)

**Configuration:**
- 50,000 vectors of 768 dimensions
- Training set: 25,000 vectors; Test set: 25,000 vectors
- 96 subspaces (PQ-96)

| Library | Training Time | Compression Time | Cosine Sim | Compression Ratio | Throughput |
|---------|:-------------:|:----------------:|:----------:|:----------------:|:----------:|
| **Vectro (Python)** | 12.4s | 3.72s | **0.8185** | 32.0x | 13,402 vec/s |
| **Faiss (C++)** | 7.5s | 0.59s | 0.8207 | 64.0x | 32,799 vec/s |

**Interpretation:**
- ✅ **Quality parity:** Vectro and Faiss achieve eq

*[truncated — see source for full prompt]*