# Adr 001 Javascript Bindings

> **Status:** Proposed
**Date:** 2026-Q3
**Author:** Wesley Scholl
**Scope:** v3.3.0 — JavaScript ecosystem interoperability

---

## Context

The v3.2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ADR-001: JavaScript / WASM Bindings

**Status:** Proposed
**Date:** 2026-Q3
**Author:** Wesley Scholl
**Scope:** v3.3.0 — JavaScript ecosystem interoperability

---

## Context

The v3.2.0 roadmap (Phase 12) identifies JavaScript/WASM bindings as a target
for the 2026 ecosystem expansion.  Concrete use cases driving this ADR:

1. **Browser-side `.vqz` reader** — allow a web client to decode a Vectro
   compressed artifact without a round-trip to a server.
2. **Node.js inference** — embed INT8 dequantization in server-side TypeScript /
   JavaScript applications (e.g. LLM inference pipelines built on LangChain.js).
3. **Edge inference** — run dequantization inside a Cloudflare Worker or similar
   V8-isolate environment where native binaries are prohibited.

The `.vqz` binary format (64-byte header + flat zstd/zlib-compressed body) is
deliberately simple: the body is a concatenation of an `int8` quantized array
and a `float32` scales array, both in C row-major order.  This means the
JavaScript runtime only needs to implement header parsing, decompression, and a
single multiply-broadcast to reconstruct float32 vectors — exactly the three-node
ONNX graph already exported by `python/onnx_export.py`.

---

## Options Considered

### Option 1 — WASM Compilation of the Mojo Quantizer

Compile `python/` Python logic or the Mojo quantizer to WebAssembly via Emscripten
or the forthcoming Mojo→WASM toolchain target.

**Pros:**
- Browser-compatible (runs inside any modern browser sandbox).
- Zero native binary distribution: ship a single `.wasm` file via npm alongside the
  TypeScript type definitions.
- Mojo's SIMD intrinsics map to WASM SIMD128 instructions.

**Cons:**
- Mojo→WASM is **not officially supported** in Mojo SDK ≤ 0.25.7; the toolchain
  target exists only as an experimental flag with no stability guarantees.
- WASM linear memory cap is 4 GB; large embedding databases (>500 M vectors) would
  need streaming from a server.
- The WASM execution model blocks the Ja

*[truncated — see source for full prompt]*