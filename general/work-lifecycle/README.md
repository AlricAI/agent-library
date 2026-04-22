# WORK LIFECYCLE

> **Version**: 2.0
**Last Updated**: 2025-11-12

## Overview

This document defines ALL work types and their lifecycles in the Brain Garden monorepo. Ev

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Work Lifecycle Documentation

**Version**: 2.0
**Last Updated**: 2025-11-12

## Overview

This document defines ALL work types and their lifecycles in the Brain Garden monorepo. Every piece of work MUST be tracked in the GROVE system with complete documentation.

## Work Type Classification

```
┌─────────────────────────────────────────────────────────────┐
│                     Work Type Decision Tree                  │
└─────────────────────────────────────────────────────────────┘

Is it NEW functionality?
├─ YES → Is it a NEW feature (multiple components, significant scope)?
│  ├─ YES → FEATURE (10-phase lifecycle, /docs/features/)
│  └─ NO → Is it an ADDITION to existing feature (post-launch)?
│     ├─ YES → ENHANCEMENT (4-phase, /docs/features/{feature}/09-enhancements/)
│     └─ NO → Re-evaluate (might be MAINTENANCE)
│
└─ NO → Is it FIXING something broken?
   ├─ YES → BUG (5-phase, /docs/bugs/)
   │
   └─ NO → Is it INTEGRATING external code?
      ├─ YES → BORG (5-phase, /docs/borg/)
      │
      └─ NO → MAINTENANCE (type-specific lifecycle, /docs/maintenance/)
          ├─ Refactoring
          ├─ Dependencies
          ├─ Performance
          ├─ Documentation
          ├─ Security
          └─ Testing
```

## Work Types Summary

| Work Type | Location | Lifecycle Phases | Quality Threshold | Example |
|-----------|----------|------------------|-------------------|---------|
| **FEATURE** | `/docs/features/` | 10 phases (00-09) | ≥85/100 | User authentication system |
| **BUG** | `/docs/bugs/` | 5 phases (00-04) | ≥80/100 | Login failure after password reset |
| **ENHANCEMENT** | `/docs/features/{feature}/09-enhancements/` | 4 phases (00-03) | ≥75/100 | Add dark mode to dashboard |
| **MAINTENANCE** | `/docs/maintenance/{type}/` | Type-specific (4-5 phases) | 75-90/100 | Refactor auth service |
| **BORG** | `/docs/borg/` | 5 phases (00-04) | ≥80/100 | Integrate Express framework |

## Feature Lifecycle

**Full Documentation**: `/FEATURE_LIFECYCLE.md`

*[truncated — see source for full prompt]*