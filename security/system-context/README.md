# System Context

> This document provides a comprehensive overview of the Tandem project for AI agents (like yourself) to understand the architecture, security model, and operational guidelines of the system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem: System Context & Agent Guide

This document provides a comprehensive overview of the Tandem project for AI agents (like yourself) to understand the architecture, security model, and operational guidelines of the system.

## 1. Project Overview

**Tandem** is a local-first, privacy-absolute AI desktop workspace. It allows users to collaborate with an AI "coworker" that has direct access to local project files, but only under strict human supervision.

- **Platform**: Cross-platform (Windows, macOS, Linux) built with Tauri v2.
- **Goal**: Mimic the collaborative experience of an AI coworking tool but with full platform support, zero lock-in, and absolute privacy.

## 2. Technical Architecture

### A. The Three-Layer Stack

1.  **Frontend (React + Vite)**: The "Glass" UI built with Tailwind CSS and Framer Motion. It handles the chat interface, file exploration, settings, and visual permission management.
2.  **Backend (Tauri/Rust)**: The security and orchestration engine. Key responsibilities:
    - **Encrypted Vault**: Storing API keys securely using AES-256-GCM encryption.
    - **LLM Routing**: Abstracting various providers (OpenRouter, Anthropic, OpenAI, Ollama) into a unified interface.
    - **Sidecar Management**: Downloading, verifying, and orchestrating the OpenCode binary.
    - **Permission Proxy**: Intercepting and presenting tool requests to the user.
    - **Operation Journaling**: Recording every file and command operation for audit and undo capability.
3.  **Sidecar (OpenCode)**: A bundled binary that acts as the "Autonomous Brain." It receives tasks and generates tool calls (read_file, write_file, run_command, etc.).

### B. Security & Isolation

- **Zero Telemetry**: No analytics, tracking, or cloud sync.
- **Network Scoping**: Traffic is restricted to local sidecar communication and user-configured LLM endpoints.
- **File Scoping**: The sidecar is strictly confined to directories explicitly granted by the user via the native file picker.

#

*[truncated — see source for full prompt]*