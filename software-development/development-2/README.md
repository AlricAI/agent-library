# DEVELOPMENT

> This guide provides comprehensive information for developers working on OpenSandbox Server, including environment setup, architecture deep-dive, testing strategies, and contribution workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Development Guide

This guide provides comprehensive information for developers working on OpenSandbox Server, including environment setup, architecture deep-dive, testing strategies, and contribution workflows.

## 📋 Table of Contents

- [Development Environment Setup](#development-environment-setup)
- [Project Structure](#project-structure)
- [Architecture Deep Dive](#architecture-deep-dive)
- [Development Workflow](#development-workflow)
- [Testing Guide](#testing-guide)
- [Working with Docker Runtime](#working-with-docker-runtime)
- [Working with Kubernetes Runtime](#working-with-kubernetes-runtime)
- [Code Style and Standards](#code-style-and-standards)
- [Debugging](#debugging)
- [Performance Optimization](#performance-optimization)
- [Contributing](#contributing)

## Development Environment Setup

### Prerequisites

- **Python 3.10+**: Check version with `python --version`
- **uv**: Install from [https://github.com/astral-sh/uv](https://github.com/astral-sh/uv)
- **Docker**: For local development and testing
- **Git**: Version control
- **IDE**: VS Code, PyCharm, or Cursor (recommended for AI assistance)

### Initial Setup

1. **Clone and Navigate**
   ```bash
   git clone https://github.com/alibaba/OpenSandbox.git
   cd OpenSandbox/server
   ```

2. **Install Dependencies**
   ```bash
   uv sync
   ```

3. **Verify Installation**
   ```bash
   uv run python -c "import fastapi; print(fastapi.__version__)"
   ```

4. **Configure Development Environment**
   ```bash
   cp opensandbox_server/examples/example.config.toml ~/.sandbox.toml
   ```

   Edit `~/.sandbox.toml` for local development:
   ```toml
   [server]
   host = "0.0.0.0"
   port = 8080
   api_key = "your-secret-api-key-change-this"

   [log]
   level = "DEBUG"

   [runtime]
   type = "docker"
   execd_image = "opensandbox/execd:v1.0.13"

   [docker]
   network_mode = "host"
   ```

5. **Run Development Server**
   ```bash
   uv run python -m opensandbox_server.main
   ```

### IDE Configuration



*[truncated — see source for full prompt]*