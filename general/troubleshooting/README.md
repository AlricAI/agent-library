# TROUBLESHOOTING

> This guide covers common issues, error messages, and solutions for ModPorter AI.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ModPorter AI Troubleshooting Guide

This guide covers common issues, error messages, and solutions for ModPorter AI.

## Table of Contents

1. [Installation Issues](#installation-issues)
2. [Configuration Issues](#configuration-issues)
3. [Agent Errors](#agent-errors)
4. [Conversion Failures](#conversion-failures)
5. [Performance Issues](#performance-issues)
6. [Docker Issues](#docker-issues)
7. [API/LLM Issues](#apillm-issues)
8. [Testing Issues](#testing-issues)

---

## Installation Issues

### Python Version Mismatch

**Error:**
```
ERROR: Package 'modporter-ai' requires Python >=3.10 but you have Python 3.9.x
```

**Solution:**
```bash
# Check Python version
python --version

# Install Python 3.10+ using pyenv (recommended)
pyenv install 3.10.13
pyenv local 3.10.13

# Or use conda
conda create -n modporter python=3.10
conda activate modporter
```

### Missing Dependencies

**Error:**
```
ModuleNotFoundError: No module named 'crewai'
```

**Solution:**
```bash
# Install all dependencies
pip install -r requirements.txt

# Or install the package in development mode
pip install -e .
```

### Java Parser Issues

**Error:**
```
ModuleNotFoundError: No module named 'javalang'
```

**Solution:**
```bash
pip install javalang
```

---

## Configuration Issues

### Missing Environment Variables

**Error:**
```
ERROR: OPENAI_API_KEY not found in environment
```

**Solution:**
```bash
# Create .env file
cp .env.example .env

# Edit .env and add your API key
echo "OPENAI_API_KEY=your-key-here" >> .env

# Or export directly
export OPENAI_API_KEY="your-key-here"
```

### Invalid Ollama Configuration

**Error:**
```
ConnectionError: Cannot connect to Ollama at http://localhost:11434
```

**Solution:**
```bash
# Check if Ollama is running
curl http://localhost:11434/api/tags

# Start Ollama if not running
ollama serve

# For Docker environments, check the Ollama container
docker ps | grep ollama
docker start ollama  # if stopped
```

### Variant Configuration Not Found

**Erro

*[truncated — see source for full prompt]*