# Modules

> Molfun's `molfun.modules` package provides a plug-and-play system for protein ML research.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Modular Architecture Guide

Molfun's `molfun.modules` package provides a plug-and-play system for protein ML research. Every major component of a structure prediction model — attention, trunk blocks, structure module, input embedder — can be swapped, combined, and extended without touching the training infrastructure.

This guide covers:

1. [Architecture overview](#architecture-overview) — how the pieces fit together
2. [Registries](#registries) — discovering and building components by name
3. [Swapping modules in pre-trained models](#swapping-modules-in-pre-trained-models) — modify OpenFold without losing weights
4. [Building custom models from scratch](#building-custom-models-from-scratch) — compose new architectures
5. [Writing your own module](#writing-your-own-module) — extend the framework
6. [Training custom models](#training-custom-models) — use Molfun's full training stack on your designs
7. [Recipes](#recipes) — concrete research scenarios

---

## Architecture overview

A protein structure prediction model in Molfun is composed of three stages:

```
Input (sequence, MSA)
       │
       ▼
  ┌──────────┐
  │ Embedder  │   aatype + relpos + MSA → initial representations
  └────┬─────┘
       │  single [B, L, D_s]  +  pair [B, L, L, D_p]
       ▼
  ┌──────────┐
  │  Blocks   │   N × (attention + pair ops + transitions)
  │ (×N)      │   Each block refines single + pair representations
  └────┬─────┘
       │  refined single + pair
       ▼
  ┌──────────────────┐
  │ Structure Module  │   representations → 3D coordinates
  └────────┬─────────┘
           │  positions [B, L, 3]
           ▼
      ┌────────┐
      │  Head   │   coordinates/repr → task prediction (affinity, loss, etc.)
      └────────┘
```

Each box is a **pluggable module** with an abstract base class, a registry, and multiple built-in implementations:

| Component | Base class | Registry | Built-in implementations |
|-----------|-----------|----------|-------------------------|
| Attention 

*[truncated — see source for full prompt]*