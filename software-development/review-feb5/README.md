# REVIEW Feb5

> **Date:** February 5, 2026
**Reviewer:** Expert Code Review (Claude)
**Codebase:** ~25,500 lines of Go across 90 files

---

## Executive Summary

Hyp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Hypergoat Codebase Review — Comprehensive Analysis & Improvement Plan

**Date:** February 5, 2026
**Reviewer:** Expert Code Review (Claude)
**Codebase:** ~25,500 lines of Go across 90 files

---

## Executive Summary

Hypergoat is a well-structured Go port of an AT Protocol AppView server. The core architecture is sound: clean separation between packages, proper use of interfaces for database abstraction, and the dynamic GraphQL-from-lexicons concept is creative. All tests pass, `go vet` is clean. However, there are several **significant issues** ranging from security concerns to architectural weaknesses that should be addressed.

**Overall Grade: B-** — Solid foundation with meaningful gaps in security, concurrency safety, and production readiness.

---

## 1. CRITICAL: Security Concerns

### 1a. SQL Injection in JSONExtract Methods

The `JSONExtract` and `JSONExtractPath` methods in **both** SQLite and PostgreSQL executors interpolate user-controlled `field` and `path` values directly into SQL strings:

```go
// sqlite/executor.go:126
func (e *Executor) JSONExtract(column, field string) string {
    return fmt.Sprintf("json_extract(%s, '$.%s')", column, field)
}
// postgres/executor.go:107
func (e *Executor) JSONExtract(column, field string) string {
    return fmt.Sprintf("%s->>'%s'", column, field)
}
```

If any caller passes user input here, it's injectable. These should sanitize/validate field names or use parameterized approaches.

### 1b. WebSocket Origin Check Disabled

```go
// subscription/handler.go:57
CheckOrigin: func(r *http.Request) bool {
    return true // Allow all origins for development
}
```

This is **fine for dev, dangerous in production**. Needs to be configurable.

### 1c. `backfillActive` Race Condition

```go
// admin/resolvers.go:299
r.backfillActive = true
go func() {
    defer func() { r.backfillActive = false }()
    ...
}()
```

This is a data race — `backfillActive` is read/written from multiple goroutines without synchronization.

*[truncated — see source for full prompt]*