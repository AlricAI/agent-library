# Architecture

> This document describes the architecture of the ANTIGRAVITY platform, including YouAndINotAI and related services.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# System Architecture

This document describes the architecture of the ANTIGRAVITY platform, including YouAndINotAI and related services.

## Overview

The ANTIGRAVITY platform consists of multiple interconnected services designed to facilitate real-world community connections while maintaining strong safety and privacy controls.

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Public Internet                          │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────────┐     ┌─────────────────┐    ┌────────────┐ │
│  │              │     │                 │    │            │ │
│  │   Browser    │────▶│  Cloudflare     │───▶│   Paper-   │ │
│  │              │     │    Pages        │    │   clip     │ │
│  └──────────────┘     └─────────────────┘    │            │ │
│                            │                 └────────────┘ │
│                            ▼                                │
│                       ┌──────────┐                          │
│                       │          │                          │
│                       │ YouAndINotAI │                      │
│                       │   Frontend   │                      │
│                       │              │                      │
│                       └──────────┘                          │
│                            │                                │
│                            ▼                                │
│  ┌──────────────┐     ┌─────────────────┐    ┌────────────┐ │
│  │              │     │                 │    │            │ │
│  │   Mobile     │────▶│  Cloudflare     │───▶│   YouAnd-  │ │
│  │   Apps       │     │    Tunnel       │    │   INotAI   │ │
│  │              │     │                 │    │   API      │ │
│  └──────────────┘     └─────────────────┘    │            │ │
│                            │     

*[truncated — see source for full prompt]*