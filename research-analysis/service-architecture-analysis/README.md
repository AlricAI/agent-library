# SERVICE ARCHITECTURE ANALYSIS

> **Generated:** 2025-08-25

## 1. Executive Summary

The core of the service crisis is a complete disconnect between the **intended architecture** (a p

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Service Architecture Analysis

**Generated:** 2025-08-25

## 1. Executive Summary

The core of the service crisis is a complete disconnect between the **intended architecture** (a proper service manager) and the **actual implementation** (uncontrolled, repeated process spawning). The project contains a well-designed service manager, `atlas_background_service.py`, but it is not being used. Instead, a chaotic method of launching processes is causing a severe process leak (37+ processes every 5 minutes).

## 2. Intended vs. Actual Architecture

### Intended Architecture

The file `atlas_background_service.py` defines a `AtlasServiceManager` class. This is a command-line tool designed for robust service management, providing:
- Centralized `start`, `stop`, `status`, and `restart` commands.
- PID file management (`atlas_service.pid`) to prevent multiple instances.
- Health monitoring and auto-recovery loops.
- Management of both the API server and background task schedulers.

This represents a standard, stable approach to managing background services.

### Actual Architecture (The "Chaos")

The system is currently suffering from a process leak where dozens of python processes are spawned repeatedly. This is caused by an external, uncontrolled mechanism (likely a cron job or a misconfigured script) that calls a script like `run.py` in a loop, without any form of process management.

This is the root cause of the instability. The system lacks a single source of truth for service control.

## 3. Root Cause of the Crisis

The root cause of the 37+ process spawning issue is the **failure to use the provided `AtlasServiceManager`**. The developer who wrote the service manager likely intended for it to be the sole entry point for the application, but this was never enforced or correctly configured in the deployment environment.

## 4. Unified Service Strategy (The Fix)

The path forward is to enforce the use of the intended architecture.

1.  **Adopt `atlas_background_service

*[truncated — see source for full prompt]*