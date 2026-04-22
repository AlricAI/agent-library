# Kw E2e Architecture

> ## Document Information

- **Version**: 1.0
- **Date**: 2025-11-26
- **Author**: Architect Agent
- **Issue**: #114 - Build KW simulation system with R

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Knowledge Worker E2E System Architecture

## Document Information

- **Version**: 1.0
- **Date**: 2025-11-26
- **Author**: Architect Agent
- **Issue**: #114 - Build KW simulation system with REAL M365 operations

---

## Executive Summary

This document specifies the architecture for integrating real M365 operations into the Knowledge Worker (KW) simulation system. The design addresses:

1. Real Entra user provisioning via existing `EntraUserManager`
2. Secure credential distribution to workers
3. Cross-worker communication with enforced internal-only boundaries
4. Transport rule enforcement via Exchange Online
5. Comprehensive resource tracking and cleanup

**Critical Design Decision**: Rename `real_m365` flag to `live_mode` throughout the codebase. The term "real" implies the alternative is "fake" or "dishonest", which is misleading - simulation mode is a valid operational mode, not a deceptive one.

---

## System Architecture

### Component Diagram

```
+------------------------------------------------------------------+
|                    KnowledgeWorkerOrchestrator                    |
|  (Deployment lifecycle: setup -> provision -> execute -> cleanup) |
+------------------------------------------------------------------+
         |                    |                    |
         v                    v                    v
+------------------+  +------------------+  +------------------+
|  SecuritySetup   |  |  UserProvisioner |  |  EndpointManager |
|  - TransportRule |  |  - EntraUserMgr  |  |  - CloudPC       |
|  - GroupManager  |  |  - GroupMembership|  |  - CLIContainer |
+------------------+  +------------------+  +------------------+
         |                    |                    |
         +--------------------+--------------------+
                              |
                              v
+------------------------------------------------------------------+
|                     WorkerCredentialStore                         |
|  (Secu

*[truncated — see source for full prompt]*