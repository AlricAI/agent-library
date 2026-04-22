# RECORDING GUIDE

> ## Overview
This guide will help you record a professional demo of Vectro using **real public embeddings** (GloVe from Stanford NLP).

**Duration:** 4

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🎬 Vectro Real-World Demo - Video Recording Guide

## Overview
This guide will help you record a professional demo of Vectro using **real public embeddings** (GloVe from Stanford NLP).

**Duration:** 4-5 minutes  
**Dataset:** GloVe 100D word embeddings (400K vocabulary)  
**Key Message:** Production-ready LLM compression with proven performance on real data

---

## 🎯 Video Structure

### Act 1: Setup (30 seconds)
**What happens:** Quick introduction and data download  
**Key message:** Easy to get started with real-world data

### Act 2: Performance (2 minutes)
**What happens:** Live quantization of 10K vectors with metrics  
**Key message:** Blazing fast throughput with real embeddings

### Act 3: Quality (1.5 minutes)
**What happens:** Accuracy analysis showing >99.9% preservation  
**Key message:** No compromise on semantic quality

### Act 4: Impact (1 minute)
**What happens:** Show compression ratios and real-world benefits  
**Key message:** Massive storage savings for production systems

---

## 📋 Pre-Recording Checklist

### Environment Setup
```bash
cd /Users/wscholl/vectro

# Ensure you're in pixi shell
pixi shell

# Verify Python dependencies
pip install numpy tqdm

# Make scripts executable
chmod +x demos/download_public_dataset.py
chmod +x demos/benchmark_public_data.py

# Clean terminal
clear
```

### Terminal Configuration
- **Theme:** Use high-contrast theme (Dracula, Nord, or Solarized Dark)
- **Font:** 16pt or larger for readability
- **Size:** Full screen or 80x24 minimum
- **Recording:** 1080p at 60fps

### Test Run
```bash
# Do a complete dry run before recording
python demos/download_public_dataset.py --dataset glove --dim 100
python demos/benchmark_public_data.py --embeddings data/glove.6B.100d.npy --sample 1000

# Verify everything works smoothly
```

---

## 🎬 Recording Script

### SCENE 1: Introduction (0:00 - 0:30)

**[Start recording - clean terminal]**

```bash
clear
```

**[Speak while typing]**

> "Hi everyone! Today I'm showing

*[truncated — see source for full prompt]*