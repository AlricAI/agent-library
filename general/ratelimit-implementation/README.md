# RATELIMIT IMPLEMENTATION

> This guide provides step-by-step instructions for implementing comprehensive rate limiting in VirtEngine.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Rate Limiting Implementation Guide

This guide provides step-by-step instructions for implementing comprehensive rate limiting in VirtEngine.

## Table of Contents

1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Quick Start](#quick-start)
4. [Detailed Integration](#detailed-integration)
5. [Configuration](#configuration)
6. [Monitoring](#monitoring)
7. [Testing](#testing)
8. [Deployment](#deployment)

---

## Overview

The rate limiting system provides:

- **Multi-layer protection**: IP, user, endpoint, and global rate limiting
- **Redis-backed storage**: Distributed rate limiting across multiple nodes
- **Graceful degradation**: Automatic rate limit adjustment under load
- **Bypass detection**: Automatic detection and banning of abusive clients
- **Comprehensive monitoring**: Prometheus metrics and alerting
- **Easy integration**: Simple HTTP and gRPC middleware

### Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Client Requests                       │
└───────────────────────┬─────────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────────┐
│            CDN/WAF (Cloudflare/AWS/Azure)                │
│              Network-level Protection                    │
└───────────────────────┬─────────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────────┐
│                HTTP/gRPC Middleware                      │
│          IP + User + Endpoint Rate Limiting              │
└───────────────────────┬─────────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────────┐
│              Redis Rate Limiter Core                     │
│        Token Bucket + Ban Management + Metrics           │
└───────────────────────┬─────────────────────────────────┘
                   

*[truncated — see source for full prompt]*