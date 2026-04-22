# Database

> This document defines the schema, relationships, and data requirements for the Marketing Dashboard database (Firebase NoSQL DB).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Database Specification

This document defines the schema, relationships, and data requirements for the Marketing Dashboard database (Firebase NoSQL DB).

## Purpose
- Specify collections, fields, constraints, and relationships.
- Document migration strategy and data integrity requirements (Firestore rules, application-level constraints).

## Overview
- The frontend stores ideas directly in Cloud Firestore using the Firebase Web SDK.
- Ideas are user-linked and isolated by path under `users/{uid}/ideas/{ideaId}`.
- Drafts are user-linked and isolated by path under `users/{uid}/drafts/{draftId}`.
- Adaptations are user-linked and isolated by path under `users/{uid}/adaptations/{adaptationId}`.
- The current ideas page only reads and writes the authenticated user's idea documents. It does not read global shared idea documents.

## Entity Relationship Summary
- `users/{uid}` is the logical user root keyed by Firebase Auth UID.
- `users/{uid}/ideas/{ideaId}` stores one persisted idea record for that authenticated user.
- `users/{uid}/drafts/{draftId}` stores one persisted draft record for that authenticated user.
- `users/{uid}/adaptations/{adaptationId}` stores one persisted multi-platform adaptation record for a draft/angle pair for that authenticated user.
- The idea document also stores `userId` so the document contents mirror the parent path and can be validated in security rules.

## Collection Definitions

### `users/{uid}/ideas/{ideaId}`
**Purpose:** Persist a single content idea created by the signed-in user.

**Required fields:**
- `topic: string`
  The idea text entered in the ideas form.
- `tone: string`
  Selected tone from the frontend ideas form.
- `audience: string`
  Selected audience from the frontend ideas form.
- `format: string`
  Selected output format from the frontend ideas form.
- `userId: string`
  Must equal the authenticated Firebase UID and the `{uid}` path segment.
- `createdAt: timestamp`
  Server timestamp written at creation time.
- `up

*[truncated — see source for full prompt]*