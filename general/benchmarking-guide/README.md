# Benchmarking Guide

> This document explains how to measure Vectro's performance and what conditions affect the numbers you'll see.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Vectro Benchmarking Guide

This document explains how to measure Vectro's performance and what conditions affect the numbers you'll see.

## Understanding Performance Modes

### Python/NumPy Fallback Mode (Always Available)

**When used:** If Mojo binary is not available or built  
**Throughput:** ~60–80K vec/s for INT8 at d=768 (depends on backend availability)

**Factors affecting throughput:**
- `squish_quant` Rust extension availability → ~3-4x speedup if installed
- NumPy BLAS configuration (OpenBLAS vs MKL → 2-3x difference)
- Batch size (larger batches → 10% faster, due to reduced Python overhead)
- Vector dimensionality (lower dims → higher throughput due to better cache locality)

**Measured (March 2026, codespace CPU, NumPy-only):**
```
d=768:   62K vec/s  (batch=10000)
d=384:   69K vec/s  (batch=10000)
d=128:   77K vec/s  (batch=10000)
```

### Mojo SIMD Mode (Requires Mojo Toolchain)

**When used:** After running `pixi run build-mojo`  
**Throughput:** 5M+ vec/s for INT8 at d=768 (Apple M-series / modern x86)

**Conditions for these numbers:**
- M-series Mac (Apple Silicon) or modern NVIDIA GPU
- Compiled Mojo binary with SIMD vectorization
- Batch size >= 1000 (smaller batches have dispatch overhead)

## Running Your Own Benchmarks

### Python/NumPy Fallback (This Environment)

Always available, no dependencies beyond numpy + pip:

```bash
python benchmarks/benchmark_python_fallback.py --output results/fallback_benchmark.json
```

Outputs JSON with:
- INT8 throughput at dimensions [128, 384, 768, 1536]
- Quality metrics (cosine similarity, compression ratio)
- Multiple batch sizes

### Mojo Binary (Requires Mojo Toolchain)

On a system with Mojo installed:

```bash
# Build the binary (one-time)
pixi run build-mojo

# Run benchmarks
pixi run benchmark
# Output format: Vec/s, cosine_sim, and compression_ratio for INT8/NF4/Binary
```

This runs: `./vectro_quantizer benchmark 10000 768`

## Interpreting Benchmark Results

### Reasonable Expectations

| Mo

*[truncated — see source for full prompt]*